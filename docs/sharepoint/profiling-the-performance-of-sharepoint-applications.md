---
title: Profilowanie wydajności aplikacji programu SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b59a3de88403300a46b7992a2dad72e3d6b59e0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864140"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilowanie wydajności aplikacji programu SharePoint

Jeśli w aplikacji programu SharePoint działają powoli lub nieefektywnie, można użyć funkcji profilowania w programie Visual Studio do identyfikowania problematycznego kod i inne elementy. Za pomocą funkcji do testowania obciążenia, można określić, jak działa aplikacja programu SharePoint przy dużym obciążeniu, np. gdy wielu użytkowników uzyskuje dostęp aplikacja jednocześnie. Uruchamiając testy wydajności sieci web, można zmierzyć, jak aplikacja działa w sieci web. Za pomocą kodowanych testów interfejsu użytkownika, można sprawdzić, czy cała aplikacja programu SharePoint, łącznie z jego interfejs użytkownika działa poprawnie. Gdy używasz tych testów jednocześnie, mogą one pomóc zidentyfikować problemy z wydajnością, przed wdrożeniem aplikacji.

## <a name="profile-tools-overview"></a>Omówienie narzędzi profilu

Profilowanie odnosi się do procesu obserwacji i rejestrowania wydajności aplikacji podczas jej działania. Przez profilowanie aplikacji, można wykryć problemy takie jak wąskich gardeł, nieefektywny kod i problemy z alokacją pamięci, które powodują, że aplikacje działają wolno lub używają zbyt dużo pamięci. Można na przykład użyć profilowania do identyfikacji punktów aktywnych w kodzie, które fragmentów kodu, które są często wywoływane i mogą spowolnić ogólną wydajność aplikacji. Po zidentyfikowaniu punktów aktywnych często można zoptymalizować lub usunąć je.

Kilku narzędzi profilowania w zintegrowanym środowisku programistycznym (IDE) służy do identyfikowania i lokalizowania tego rodzaju problemów z wydajnością. Te narzędzia działają tak samo dla projektów programu SharePoint, jak w przypadku innych rodzajów projektów programu Visual Studio. Kreator wydajności narzędzi profilowania prowadzi poprzez tworzenie sesji wydajności, która korzysta z testów, które określisz. Sesja wydajności jest zestaw danych konfiguracji, który służy do zbierania informacji o wydajności z aplikacji, wraz z wynikami jednej lub więcej tras profilowania. Sesje pomiaru wydajności są przechowywane w folderze projektu i można wyświetlić je w **Eksplorator wydajności**. Aby uzyskać więcej informacji, zobacz [metodami zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md).

Po utworzeniu i uruchomieniu analizy profilu w swojej aplikacji raport zawiera szczegółowe informacje o jego wydajności. Ten raport może zawierać elementy, takie jak wykres użycia procesora CPU w czasie, stos wywołań funkcji hierarchicznych lub drzewo wywołań. Dokładna zawartość raportu może się różnić w zależności od typu testu, który zostanie uruchomiony, pobieranie próbek lub Instrumentacja. Aby uzyskać więcej informacji, zobacz [Przegląd raportów narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Wydajność sesji procesu

Aby profilować aplikację, uruchom za pomocą Kreatora wydajności narzędzi profilowania do utworzenia sesji wydajności. Na pasku menu wybierz **analizy**, **Uruchom Kreatora wydajności**. Po ukończeniu kreatora, możesz wprowadzić wymagane informacje dotyczące sesji wydajności, takich jak metoda profilowania, która ma i aplikacji, które powinny być profilowane. Aby uzyskać więcej informacji, zobacz [jak: Profilowanie witryny sieci Web lub aplikacji sieci Web za pomocą Kreatora wydajności](http://go.microsoft.com/fwlink/?LinkId=224692). Jako alternatywę można użyć opcji wiersza polecenia, można skonfigurować i uruchomić sesję wydajności. Aby uzyskać więcej informacji, zobacz [przy użyciu Profiling Tools z wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=224703). Jeśli chcesz ręcznie skonfigurować każdy aspekt sesji pomiaru wydajności, zobacz [jak: Ręczne tworzenie sesji wydajności przy użyciu narzędzi do profilowania](http://go.microsoft.com/fwlink/?LinkId=224691). Można również utworzyć sesję wydajności z testu jednostkowego w **wyników testu** okna, otwierając menu skrótów dla testu jednostkowego, a następnie wybierając **Tworzenie sesji kontroli wydajności**.

Po skonfigurowaniu sesji wydajności, Konfiguracja sesji jest zapisywana, serwer jest skonfigurowany do dostarczania danych profilowania i aplikacja zostanie uruchomiona. Jak korzystasz z aplikacji, dane wydajności są zapisywane w pliku dziennika. Sesje pomiaru wydajności są wymienione w **Eksplorator wydajności** w obszarze **cele** folderu. Po zakończeniu sesji wydajności, jego raport pojawia się w **raporty** folderu w **Eksplorator wydajności**. Aby wyświetlić raport, otwórz go w **Eksplorator wydajności**. Aby wyświetlić lub skonfigurować właściwości sesji wydajności, otwórz jego menu skrótów na liście **Eksplorator wydajności**, a następnie wybierz **właściwości**. Aby uzyskać więcej informacji na temat określonych właściwości sesji wydajności, zobacz [Konfigurowanie sesji pomiaru wydajności dla narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224694). Aby uzyskać informacje o interpretowaniu wyników sesji pomiaru wydajności, zobacz [analizowanie danych narzędzi profilowania](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-test"></a>Test obciążeniowy

Tworząc testy obciążenia i testy wydajności sieci web w programie Visual Studio można analizować wydajność obciążenia aplikacji. Po utworzeniu testu obciążenia w programie Visual Studio, określasz kombinację czynników, o nazwie scenariusz, aby przetestować aplikację. Czynniki te obejmują wzór obciążenia, model testu mieszanego, test mieszany, mieszany profil sieciowy i mieszaną przeglądarkę sieci web. Scenariusze testów obciążenia może zawierać zarówno testy jednostkowe, jak i testy wydajności sieci web.

Rysunek 1: Przykład wyników testowania obciążenia

![Uruchamianie testu obciążenia widoku wykresy](../sharepoint/media/load-webgraphs.png "widoku wykresy uruchomionego testu obciążenia")

Testy wydajności sieci Web zasymulować, jak użytkownik końcowy może wchodzić w interakcje przy użyciu aplikacji programu SharePoint. Można utworzyć testy wydajności sieci web poprzez rejestrowanie żądań HTTP w sesji przeglądarki lub za pomocą **rejestratora testów wydajności sieci Web**. Żądania sieci web pojawiają się w **edytora testów wydajności sieci Web** po zakończeniu sesji przeglądarki. Następnie można debugować wyniki w parametrze **podglądu wyników testu wydajności sieci Web**. Można również ręcznie budować testy wydajności sieci web za pomocą **edytora testów wydajności sieci Web**.

## <a name="test-user-interfaces"></a>Testowanie interfejsów użytkownika

Kodowane testy interfejsu użytkownika automatycznie uruchamiają aplikację SharePoint przez interfejs użytkownika (UI). Te testy obejmują formantu UI, takie jak przyciski i menu, aby sprawdzić, czy działają poprawnie. Tego rodzaju testy są szczególnie przydatne, jeśli sprawdzanie poprawności lub inna logika jest wykonywana w Interfejsie użytkownika, takie jak na stronie sieci web. Kodowane testy interfejsu użytkownika można również użyć do automatyzacji testów ręcznych. Możesz tworzyć kodowane testy interfejsu użytkownika dla aplikacji programu SharePoint w taki sam sposób jak tworzysz testy dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Profil aplikacji programu SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Pokazuje, jak wykonać analizę profilu pobierania próbek na aplikacji programu SharePoint.|
|[Testowanie wydajności aplikacji sieci przed wydaniem](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|W tym artykule opisano sposób tworzenia testów obciążenia, które ułatwiają test obciążeniowy aplikacji programu SharePoint.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W tym artykule opisano, jak znaleźć błędy logiczne w kodzie za pomocą testów jednostkowych.|
|[Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|W tym artykule opisano sposób testowania interfejsu użytkownika aplikacji programu SharePoint.|

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Podnoszenie jakości kodu](../test/improve-code-quality.md)