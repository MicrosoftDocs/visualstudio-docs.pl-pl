---
title: Weryfikowanie i debugowanie kodu programu SharePoint | Dokumentacja firmy Microsoft
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1705e77472ba9b8fa7a01d047c0aadaf342b7932
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916838"
---
# <a name="verify-and-debug-sharepoint-code"></a>Sprawdź i możliwe jest debugowanie kodu programu SharePoint
Używając funkcji IntelliTrace i testów jednostkowych, można łatwiej debugować rozwiązania przeznaczone na platformę SharePoint i gwarantować poprawne działanie wszystkich zawartych w nich metod. Te funkcje można użyć dla projektów programu SharePoint w programie Visual Studio, wykonując te same procedury jak w przypadku innych typów projektów.

## <a name="intellitrace"></a>IntelliTrace
Za pomocą funkcji IntelliTrace można określić nie tylko bieżący stan swojego rozwiązania programu SharePoint, ale także zdarzeń, które wystąpiły w przeszłości, oraz kontekstu, w którym miały one miejsce. W rozwiązaniu programu SharePoint można przechodzić do przodu i z powrotem w różne punkty w czasie, gdzie zostały zarejestrowane określone zdarzenia, oraz przeglądać stany i wartości zmiennych w każdym z tych punktów. Za pomocą tej dynamicznej nawigacji można szybciej i łatwiej debugować rozwiązania programu SharePoint bez konieczności ustawiania licznych punktów przerwania. Można także zapisać sesję debugowania do dziennika IntelliTrace (*.iTrace*) plik, otwórz go w dalszej części programu Visual Studio Enterprise i wykonać debugowanie po awarii. *.ITrace* plik zawiera szczegółowe informacje, kiedy i gdzie wystąpiły konkretne błędy programu SharePoint, dzięki czemu można łatwiej ustalić przyczyny błędów. Informacje przedstawione w *.iTrace* pliku jest podzbiorem pełnego dziennika błędów tworzonego Unified Logging System (ULS) w programie SharePoint. Wśród tych informacji są zdarzenia specyficzne dla programu SharePoint, np. otwarcie lub zamknięcie profilu użytkownika oraz załadowanie, odczyt i modyfikacja właściwości projektu programu SharePoint. Można określić, które zdarzenia funkcja IntelliTrace ma rejestrować. Aby uzyskać więcej informacji, zobacz [używanie zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).

Gdy w programie SharePoint wystąpi błąd, w oknie dialogowym tego błędu pojawia się „identyfikator korelacji”. Identyfikatory korelacji można również uzyskać ze zdarzeń, które są wymienione w *.iTrace* pliku. Aby wyświetlić listę wszystkich zaistniałych zdarzeń z podanym Identyfikatorem korelacji, możesz wprowadzić identyfikator w **analizy** sekcji na stronie podsumowania funkcji IntelliTrace. W sekcji można wskazać, czy mają być wyświetlane tylko nazwy zaistniałych zdarzeń czy też nazwy razem z informacjami o wywołaniach, takimi jak nazwy funkcji, punkty wejścia i wyjścia, parametry i zwracane wartości.

W funkcji IntelliTrace można uzyskać zdarzenia programu Visual Studio, wybierając **F5** klucza. Jednak w przypadku zdarzeń specyficznych dla programu SharePoint do zbierania danych funkcji IntelliTrace w rozwiązaniach programu SharePoint należy używać programu Microsoft Monitoring Agent. To narzędzie służy do zbierania danych funkcji IntelliTrace i tworzy *.iTrace* plików dla aplikacji wdrożonych poza programem Visual Studio. Aby uzyskać więcej informacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md) i [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Test jednostkowy
Ułatwieniem przy wyszukiwaniu błędów w kodzie są testy jednostkowe, ponieważ można w nich zapisać kod testów i wykonywać go wewnątrz metod testowych. Metody te zawierają puste zmienne oraz instrukcję Assert, za pomocą której można weryfikować logikę i funkcjonalność projektu w oparciu o model obiektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Obsługa Microsoft Fakes framework
Projekty programu SharePoint obsługują Microsoft Fakes. To środowisko izolacji, w którym można tworzyć oparte na delegatach zastępcze klasy i podkładki testowe w aplikacjach bazujących na środowisku .NET Framework. Środowisko Fakes pozwala generować, obsługiwać i wprowadzać fikcyjne implementacje do testów jednostkowych. Zastępcze klasy i podkładki odizolowują testy jednostkowe od środowiska. Zastępcze klasy umożliwiają testowanie kodu, który wykorzystuje interfejsy lub niezapieczętowane klasy z metodami możliwymi do zastąpienia. Z kolei podkładki umożliwiają przekierowywanie ustalonych wywołań do zapieczętowanych klas z metodami statycznymi lub niedającymi się zastąpić do alternatywnymi implementacji podkładek. Delegaci z typami zastępczych klas i typami podkładek umożliwiają dynamiczne dostosowywanie zachowań poszczególnych elementów członkowskich takich zastępczych klas. Aby uzyskać więcej informacji, zobacz [izolując kod w ramach testu, with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Pokrewne artykuły:

|Tytuł|Opis|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Opis sposobów łatwiejszego debugowania rozwiązań programu Visual Studio za pomocą funkcji IntelliTrace.|
|[Przewodnik: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Wyjaśnienie, jak znaleźć błędy kodu w projekcie programu SharePoint przy użyciu funkcji IntelliTrace.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W tym artykule opisano, jak znaleźć błędy logiczne w kodzie za pomocą testów jednostkowych.|

## <a name="see-also"></a>Zobacz także

- [Podnoszenie jakości kodu](../test/improve-code-quality.md)