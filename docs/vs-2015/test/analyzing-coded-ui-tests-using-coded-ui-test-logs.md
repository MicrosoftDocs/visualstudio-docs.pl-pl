---
title: Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3ebb18aaff78d9782b6210e25bcd697d21c8570
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660766"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analiza dzienników zakodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dzienniki kodowanych testów interfejsu użytkownika filtru i rejestrowania ważnych informacji o kodowanych przebiegach testów interfejsu użytkownika.

 **Requirements**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Dlaczego warto to zrobić?
 Dzienniki są prezentowane w formacie umożliwiającym szybkie Debugowanie problemów.

## <a name="how-do-i-do-this"></a>Jak mogę to zrobić?

### <a name="step-1-enable-logging"></a>Krok 1. Włączanie rejestrowania
 W zależności od scenariusza należy użyć jednej z następujących metod, aby włączyć dziennik.

- Docelowa .NET Framework w wersji 4 bez pliku App. config obecnego w projekcie testowym

  - Otwórz plik **QTAgent32_40. exe. config** .

    Domyślnie ten plik znajduje się w **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12 \ Common7\IDE**.

    Zmodyfikuj wartość EqtTraceLevel na żądany poziom dziennika.

    Zapisz plik.

- Docelowa .NET Framework wersja 4,5 bez pliku App. config obecnego w projekcie testowym

  - Otwórz plik **QTAgent32. exe. config** .

    Domyślnie ten plik znajduje się w **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12 \ Common7\IDE**.

    Zmodyfikuj wartość EqtTraceLevel na żądany poziom dziennika.

    Zapisz plik.

- Plik App. config znajduje się w projekcie testowym

  - Otwórz plik App. config w projekcie.

    Dodaj następujący kod w węźle Konfiguracja:

    `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`

- Włącz rejestrowanie na samym kodzie testu

  - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState. AllActionSnapshot;

### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2. Uruchamianie kodowanego testu interfejsu użytkownika i Wyświetlanie dziennika
 Po uruchomieniu kodowanego testu interfejsu użytkownika z modyfikacjami w pliku **QTAgent32. exe. config** na miejscu zostanie wyświetlony link danych wyjściowych w wynikach programu Test Explorer. Pliki dzienników są tworzone nie tylko wtedy, gdy test zakończy się niepowodzeniem, ale również dla testów zakończonych powodzeniem, gdy poziom śledzenia jest ustawiony na wartość "verbose".

1. Z menu **test** wybierz pozycję **Windows** , a następnie wybierz pozycję **Eksplorator testów**.

2. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

3. W Eksploratorze testów wybierz kodowany test interfejsu użytkownika, który chcesz uruchomić, otwórz jego menu skrótów, a następnie wybierz polecenie **Uruchom wybrane testy**.

     Testy automatyczne zostaną uruchomione i wskażą, czy zakończyły się powodzeniem, czy nie.

    > [!TIP]
    > Aby wyświetlić Eksploratora testów z **menu test**, wskaż pozycję **Windows** , a następnie wybierz **Eksplorator testów**.

4. Wybierz łącze **dane wyjściowe** w wynikach programu Test Explorer.

     ![Link wyjściowy w Eksploratorze testów](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")

     Spowoduje to wyświetlenie danych wyjściowych dla testu, który będzie zawierać link do dziennika akcji.

     ![Wyniki i linki wyjściowe z kodowanego testu interfejsu użytkownika](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")

5. Wybierz łącze UITestActionLog. html.

     Dziennik jest wyświetlany w przeglądarce internetowej.

     ![Plik dziennika kodowanego testu interfejsu użytkownika](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")

## <a name="q--a"></a>p & A

### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>P: co się stało z kluczem EnableHtmlLogger?
 W poprzednich wersjach programu Visual Studio istnieją dwa dodatkowe ustawienia konfiguracji umożliwiające włączenie rejestratora HTML w kodowanym teście interfejsu użytkownika:

```

<add key="EnableHtmlLogger" value="true"/>

<add key="EnableSnapshotInfo" value="true"/>

```

 Oba te ustawienia zostały zaniechane od programu Visual Studio 2012. EqtTraceLevel jest jedynym ustawieniem, które jest wymagane do modyfikacji w celu włączenia HtmlLogger.

## <a name="see-also"></a>Zobacz też
 [Korzystanie z automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [: uruchamianie testów z Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
