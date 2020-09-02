---
title: Weryfikowanie i debugowanie kodu programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b57e07245631d37594d66ea7907b16efd817b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "63008256"
---
# <a name="verify-and-debug-sharepoint-code"></a>Weryfikowanie i debugowanie kodu programu SharePoint
Używając funkcji IntelliTrace i testów jednostkowych, można łatwiej debugować rozwiązania przeznaczone na platformę SharePoint i gwarantować poprawne działanie wszystkich zawartych w nich metod. Możesz użyć tych funkcji dla projektów programu SharePoint w programie Visual Studio, wykonując te same procedury jak w przypadku innych typów projektów.

## <a name="intellitrace"></a>IntelliTrace
Za pomocą funkcji IntelliTrace można określić nie tylko bieżący stan swojego rozwiązania programu SharePoint, ale także zdarzeń, które wystąpiły w przeszłości, oraz kontekstu, w którym miały one miejsce. W rozwiązaniu programu SharePoint można przechodzić do przodu i z powrotem w różne punkty w czasie, gdzie zostały zarejestrowane określone zdarzenia, oraz przeglądać stany i wartości zmiennych w każdym z tych punktów. Za pomocą tej dynamicznej nawigacji można szybciej i łatwiej debugować rozwiązania programu SharePoint bez konieczności ustawiania licznych punktów przerwania. Możesz również zapisać sesję debugowania w pliku dziennika IntelliTrace (*. iTrace*), otworzyć go później w Visual Studio Enterprise i wykonać debugowanie po awarii. Plik *. iTrace* zawiera szczegółowe informacje o tym, kiedy i gdzie wystąpią konkretne błędy programu SharePoint, dzięki czemu można łatwiej ustalić przyczynę błędów. Informacje zawarte w pliku *. iTrace* to podzestaw kompletnego dziennika błędów, który tworzy system Unified rejestrowania (ULS) w programie SharePoint. Wśród tych informacji są zdarzenia specyficzne dla programu SharePoint, np. otwarcie lub zamknięcie profilu użytkownika oraz załadowanie, odczyt i modyfikacja właściwości projektu programu SharePoint. Można określić, które zdarzenia funkcja IntelliTrace ma rejestrować. Aby uzyskać więcej informacji, zobacz [Korzystanie z zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md).

Gdy w programie SharePoint wystąpi błąd, w oknie dialogowym tego błędu pojawia się „identyfikator korelacji”. Można również uzyskać identyfikatory korelacji z zdarzeń, które są wymienione w pliku *. iTrace* . Aby wyświetlić listę wszystkich zdarzeń, które wystąpiły z danym IDENTYFIKATORem korelacji, można wprowadzić identyfikator w sekcji **Analiza** na stronie podsumowania IntelliTrace. W sekcji można wskazać, czy mają być wyświetlane tylko nazwy zaistniałych zdarzeń czy też nazwy razem z informacjami o wywołaniach, takimi jak nazwy funkcji, punkty wejścia i wyjścia, parametry i zwracane wartości.

Zdarzenia programu Visual Studio można uzyskać w IntelliTrace, wybierając klawisz **F5** . Jednak w przypadku zdarzeń specyficznych dla programu SharePoint do zbierania danych funkcji IntelliTrace w rozwiązaniach programu SharePoint należy używać programu Microsoft Monitoring Agent. To narzędzie zbiera dane IntelliTrace i tworzy pliki *iTrace* dla aplikacji, które są wdrażane poza programem Visual Studio. Aby uzyskać więcej informacji, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md) i [using IntelliTrace autonomiczny moduł zbierający](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Test jednostkowy
Ułatwieniem przy wyszukiwaniu błędów w kodzie są testy jednostkowe, ponieważ można w nich zapisać kod testów i wykonywać go wewnątrz metod testowych. Metody te zawierają puste zmienne oraz instrukcję Assert, za pomocą której można weryfikować logikę i funkcjonalność projektu w oparciu o model obiektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Unit Testing Code](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Obsługa struktury sztucznych firmy Microsoft
Projekty programu SharePoint obsługują Microsoft Fakes. To środowisko izolacji, w którym można tworzyć oparte na delegatach zastępcze klasy i podkładki testowe w aplikacjach bazujących na środowisku .NET Framework. Środowisko Fakes pozwala generować, obsługiwać i wprowadzać fikcyjne implementacje do testów jednostkowych. Zastępcze klasy i podkładki odizolowują testy jednostkowe od środowiska. Zastępcze klasy umożliwiają testowanie kodu, który wykorzystuje interfejsy lub niezapieczętowane klasy z metodami możliwymi do zastąpienia. Z kolei podkładki umożliwiają przekierowywanie ustalonych wywołań do zapieczętowanych klas z metodami statycznymi lub niedającymi się zastąpić do alternatywnymi implementacji podkładek. Delegaci z typami zastępczych klas i typami podkładek umożliwiają dynamiczne dostosowywanie zachowań poszczególnych elementów członkowskich takich zastępczych klas. Aby uzyskać więcej informacji, zobacz [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md)elementów sztucznych firmy Microsoft.

## <a name="related-articles"></a>Pokrewne artykuły:

|Tytuł|Opis|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Opis sposobów łatwiejszego debugowania rozwiązań programu Visual Studio za pomocą funkcji IntelliTrace.|
|[Przewodnik: debugowanie aplikacji SharePoint przy użyciu IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Wyjaśnienie, jak znaleźć błędy kodu w projekcie programu SharePoint przy użyciu funkcji IntelliTrace.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Opisuje, jak znaleźć błędy logiki w kodzie przy użyciu testów jednostkowych.|

## <a name="see-also"></a>Zobacz też

- [Podnoszenie jakości kodu](../test/improve-code-quality.md)