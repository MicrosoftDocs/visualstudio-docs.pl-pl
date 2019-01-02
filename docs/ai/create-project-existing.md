---
---
# <a name="create-an-ai-project-from-existing-code"></a>Tworzenie projektu sztucznej Inteligencji z istniejącego kodu

Po [zainstalowany program Visual Studio Tools for AI](installation.md), można łatwo przenieść istniejący kod języka Python do projektu programu Visual Studio.

> [!Important]
> Proces opisany w tym miejscu nie Przenieś lub skopiuj oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, zduplikowane najpierw folder.

1. Uruchom program Visual Studio i wybierz **Plik > Nowy > Projekt**.

2. W **nowy projekt** okno dialogowe, wyszukaj "**narzędzia si**", wybierz opcję "**kodu z istniejących Python**" szablonu, należy nadać projektowi nazwę i lokalizację, a następnie wybierz pozycję **OK**.

   ![Nowy projekt z istniejącego kodu, krok 1](media/create-project-existing/new-ai-project.png)

3. W oknie kreatora należy ustawić ścieżkę do istniejącego kodu, ustawić filtr dla typów plików i określić wszelkie ścieżki wyszukiwania, które projektu wymaga, a następnie wybierz **OK**. Jeśli nie wiesz, jakie wyszukiwania ścieżki, pozostaw to pole puste.

   ![Nowy projekt z istniejącego kodu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Jeśli istniejący kod jest częścią projektu Azure Machine Learning, **folderu jest usługi Azure Machine Learning** do zapewnienia pomyślnego konwersja ważne szczegóły konfiguracji usługi Azure Machine Learning, takie jak eksperymentowania konta, obszar roboczy, konteksty używać wystąpień obliczeniowych, i inne.

4. Aby ustawić plik startowy, zlokalizuj plik w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, a następnie wybierz **Ustaw jako plik startowy**.

5. Uruchom program, naciskając klawisz **Ctrl**+**F5** lub wybierając **Debuguj > Uruchom bez debugowania**.

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Zobacz także

- [Ręcznie Zidentyfikuj istniejącego środowiska Python](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)