---
title: Analiza dzienników zakodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ec1025eaa53861fae2cf92395d8842854649fa8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591219"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analizowanie zakodowanych testów interfejsu użytkownika przy użyciu kodowanych dzienników testów interfejsu użytkownika

Kodowane dzienniki testów interfejsu użytkownika filtrują i rejestrują ważne informacje o kodowanych przebiegach testu interfejsu użytkownika. Dzienniki są prezentowane w formacie, który pozwala na problemy debugowania szybko.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Krok 1: Włącz rejestrowanie

W zależności od scenariusza użyj jednej z następujących metod, aby włączyć dziennik:

- Jeśli w projekcie testowym nie ma pliku *App.config:*

   1. Określ, który proces *QTAgent\*.exe* jest uruchamiany po uruchomieniu testu. Jednym ze sposobów, aby to zrobić, jest oglądanie karty **Szczegóły** w **Menedżerze zadań**systemu Windows .

   2. Otwórz odpowiedni plik *.config* z folderu *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<>\\ \<edition>\Common7\IDE* folder. Na przykład, jeśli proces, który jest uruchamiany jest *QTAgent_40.exe*, otwórz *QTAgent_40.exe.config*.

   2. Zmodyfikuj wartość **EqtTraceLevel** do żądanego poziomu dziennika.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Zapisz plik.

- Jeśli w projekcie testowym znajduje się plik *App.config:*

  - Otwórz plik *App.config* w projekcie i dodaj następujący kod w węźle konfiguracji:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Włącz rejestrowanie z samego kodu testowego:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Uruchom kodowany test interfejsu użytkownika i wyświetl dziennik

Po uruchomieniu zakodowany test interfejsu użytkownika z modyfikacjami pliku *\*QTAgent .exe.config* w miejscu, zobaczysz łącze wyjściowe w **wynikach Eksploratora testów.** Pliki dziennika są tworzone nie tylko wtedy, gdy test zakończy się niepowodzeniem, ale także dla pomyślnych testów, gdy poziom śledzenia jest ustawiony na **pełne**.

1. W menu **Test** wybierz polecenie **Windows,** a następnie wybierz pozycję **Eksplorator testów**.

2. W menu **Kompilacja** wybierz polecenie **Build Solution**.

3. W **Eksploratorze testów**wybierz kodowany test interfejsu użytkownika, który chcesz uruchomić, otwórz menu skrótów, a następnie wybierz polecenie **Uruchom testy wybierz**.

     Testy automatyczne są uruchamiane i wskazują, czy przeszły, czy nie powiodły się.

    > [!TIP]
    > Aby wyświetlić **Eksploratora testów,** wybierz pozycję **Test** > **Windows**, a następnie wybierz pozycję **Eksplorator testów**.

4. Wybierz **łącze Dane wyjściowe** w wynikach **Eksploratora testów.**

     ![Łącze wyjściowe w Eksploratorze testów](../test/media/cuit_htmlactionlog1.png)

     Spowoduje to wyświetlenie danych wyjściowych dla testu, który zawiera łącze do dziennika akcji.

     ![Wyniki i łącza wyjściowe z zakodowany test interfejsu użytkownika](../test/media/cuit_htmlactionlog2.png)

5. Wybierz łącze *UITestActionLog.html.*

     Dziennik jest wyświetlany w przeglądarce internetowej.

     ![Kodowany plik dziennika testu interfejsu użytkownika](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Jak: Uruchamianie testów z programu Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
