---
title: Analiza dzienników zakodowanych testów interfejsu użytkownika
description: Dowiedz się więcej na temat dzienników kodowanych testów interfejsu użytkownika, które filtrują i zapisują ważne informacje dotyczące przebiegów kodowanego testu interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3dcbb1bdfd89ae13df5174b6502dc6e89437a468
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442498"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika

Dzienniki kodowanych testów interfejsu użytkownika filtru i rejestrowania ważnych informacji o kodowanych przebiegach testów interfejsu użytkownika. Dzienniki są prezentowane w formacie umożliwiającym szybkie Debugowanie problemów.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Krok 1. Włączanie rejestrowania

W zależności od scenariusza należy użyć jednej z następujących metod, aby włączyć dziennik:

- Jeśli w projekcie testowym nie istnieje plik *App.config* :

   1. Określ, który proces *QTAgent \* . exe* jest uruchamiany po uruchomieniu testu. Jednym ze sposobów jest Obejrzyj kartę **szczegóły** w **Menedżerze zadań** systemu Windows.

   2. Otwórz odpowiedni plik *config* w folderze *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE* . Na przykład jeśli proces, który jest uruchomiony, jest *QTAgent_40.exe*, Otwórz *QTAgent_40.exe.config*.

   2. Zmodyfikuj wartość **EqtTraceLevel** na żądany poziom dziennika.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Zapisz plik.

- Jeśli istnieje plik *App.config* obecny w projekcie testowym:

  - Otwórz plik *App.config* w projekcie i Dodaj następujący kod w węźle Konfiguracja:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Włącz rejestrowanie z poziomu kodu testu:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2. Uruchamianie kodowanego testu interfejsu użytkownika i Wyświetlanie dziennika

Po uruchomieniu kodowanego testu interfejsu użytkownika przy użyciu modyfikacji w pliku *QTAgent \*.exe.config* , w wynikach programu **Test Explorer** zostanie wyświetlony link danych wyjściowych. Pliki dzienników są tworzone nie tylko wtedy, gdy test zakończy się niepowodzeniem, ale również dla testów zakończonych powodzeniem, gdy poziom śledzenia ma wartość **pełne**.

1. Z menu **test** wybierz pozycję **Windows** , a następnie wybierz pozycję **Eksplorator testów**.

2. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

3. W **Eksploratorze testów** wybierz kodowany test interfejsu użytkownika, który chcesz uruchomić, otwórz jego menu skrótów, a następnie wybierz polecenie **Uruchom wybrane testy**.

     Testy automatyczne są uruchamiane i wskazują, czy zakończyły się powodzeniem, czy nie.

    > [!TIP]
    > Aby wyświetlić **Eksplorator testów**, wybierz **Test** pozycję  >  **Windows** test, a następnie wybierz **Eksplorator testów**.

4. Wybierz łącze **dane wyjściowe** w wynikach programu **Test Explorer** .

     ![Link wyjściowy w Eksploratorze testów](../test/media/cuit_htmlactionlog1.png)

     Spowoduje to wyświetlenie danych wyjściowych testu zawierającego link do dziennika akcji.

     ![Wyniki i linki wyjściowe z kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog2.png)

5. Wybierz łącze *UITestActionLog.html* .

     Dziennik jest wyświetlany w przeglądarce internetowej.

     ![Plik dziennika kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Instrukcje: uruchamianie testów z Microsoft Visual Studio](/previous-versions/ms182470(v=vs.140))