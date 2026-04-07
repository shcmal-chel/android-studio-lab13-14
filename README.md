# Лабораторная работа №13-14. ViewModel и архитектура Android-приложений

## Цель работы:

Познакомиться с архитектурными компонентами Android Jetpack,
научиться использовать ViewModel для управления состоянием UI и сохранения данных
при изменении конфигурации устройства (поворот экрана, смена темы и т.д.).
Разработать игру с подсчётом очков, которая не теряет данные при повороте экрана.

___

## Теоретическая часть

**Архитектура приложения** — это набор правил проектирования, которые
определяют структуру вашего приложения. Подобно чертежу дома, архитектура
обеспечивает надёжность, гибкость, масштабируемость и удобство поддержки кода на
долгие годы.

## Зачем это нужно?

* Легко добавлять новые функции
* Код можно тестировать
* Легко находить и исправлять баги
* Несколько разработчиков могут работать над одним проектом


___

## Примеры кода

```kotlin
    @Test
    fun gameViewModel_AllWordsGuessed_UiStateUpdatedCorrectly(){
        var expectedScore = 0
        var currentGameUiState = viewModel.uiState.value
        var correctPlayerWord = getUnscrambledWord(currentGameUiState.currentScrambledWord)
        repeat(MAX_NO_OF_WORDS) {
            expectedScore += SCORE_INCREASE
            viewModel.updateUserGuess(correctPlayerWord)
            viewModel.checkUserGuess()
            currentGameUiState = viewModel.uiState.value
            correctPlayerWord = getUnscrambledWord(currentGameUiState.currentScrambledWord)
            assertEquals(expectedScore, currentGameUiState.score)
        }
        assertEquals(MAX_NO_OF_WORDS, currentGameUiState.currentWordCount)
        assertTrue(currentGameUiState.isGameOver)
    }
```
## Автор
Шмаль Иван Максимович
## Группа
ИСП-232
## Лицензия
Проект создан в учебных целях.
