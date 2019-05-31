---
title: Analiza dzienników zakodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a485f58e477d56625bc5ac88a014fc730057b97c
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432311"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analizowanie coded UI kodowanych testów przy użyciu dzienników testu interfejsu użytkownika

Kodowane filtr dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje dotyczące Twojego kodowanego testu interfejsu użytkownika. Dzienniki są prezentowane w formacie, który umożliwia szybkie debugowanie problemów.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Krok 1. Włącz rejestrowanie

Zależnie od scenariusza należy użyć jednej z następujących metod Aby włączyć dziennik:

- Jeśli ma nie *App.config* plik istnieje w projekcie testu:

   1. Określenie *QTAgent\*.exe* proces nie jest uruchamiany po uruchomieniu testu. Jednym ze sposobów, aby zrobić to jest, aby obejrzeć **szczegóły** kartę w Windows **Menedżera zadań**.
   
   2. Otwórz odpowiedni *.config* plik wchodzącej w skład *% ProgramFiles (x86) %\Microsoft Visual Studio\\\<wersji >\\\<edition > \Common7\IDE* folderu. Na przykład, jeśli proces działa jest *QTAgent_40.exe*, otwórz *QTAgent_40.exe.config*.

   2. Zmodyfikuj wartość **EqtTraceLevel** na poziom dziennika, które chcesz.
   
      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Zapisz plik.

- W przypadku *App.config* plik istnieje w projekcie testu:

    - Otwórz *App.config* plik w projekcie, a następnie dodaj następujący kod w węźle Konfiguracja:

      ```xml
      <system.diagnostics>
        <switches>
          <add name="EqtTraceLevel" value="4" />
        </switches>
      </system.diagnostics>`
      ```

- Włączanie rejestrowania z sam kod testu:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2. Uruchom kodowany test interfejsu użytkownika, aby wyświetlić dziennik

Po uruchomieniu kodowanego testu interfejsu użytkownika ze zmianami do *QTAgent\*. exe.config* pliku w miejscu, zobacz dane wyjściowe link **Eksploratora testów** wyników. Pliki dziennika są tworzone, nie tylko w przypadku, gdy test kończy się niepowodzeniem ale także w przypadku udanych testów podczas poziom śledzenia jest równa **pełne**.

1. Na **testu** menu, wybierz **Windows** , a następnie wybierz **Eksplorator testów**.

2. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

3. W **Eksploratora testów**, wybierz kodowanego testu interfejsu użytkownika, aby uruchomić, otwórz jego menu skrótów, a następnie wybierz **Uruchom wybrane testy**.

     Testy automatyczne uruchamianie i wskazują one powodzeniem lub niepowodzeniem.

    > [!TIP]
    > Aby wyświetlić **Eksplorator testów**, wybierz **testu** > **Windows**, a następnie wybierz **Eksplorator testów**.

4. Wybierz **dane wyjściowe** łącze w **Eksplorator testów** wyników.

     ![Link danych wyjściowych w Eksploratorze testów](../test/media/cuit_htmlactionlog1.png)

     Spowoduje to wyświetlenie danych wyjściowych dla testu, który zawiera łącze do dziennika akcji.

     ![Wyniki i łącza danych wyjściowych z kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog2.png)

5. Wybierz *UITestActionLog.html* łącza.

     Dziennik jest wyświetlany w przeglądarce sieci web.

     ![Plik dziennika w kodowanych testów interfejsu użytkownika](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Instrukcje: Uruchamianie testów z programu Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
