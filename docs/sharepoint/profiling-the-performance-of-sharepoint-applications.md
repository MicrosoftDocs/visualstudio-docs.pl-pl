---
title: Profilowanie wydajności aplikacji programu SharePoint | Microsoft Docs
description: Profile wydajność aplikacji programu SharePoint, jeśli działają wolno lub nieefektywnie. Użyj funkcji profilowania programu Visual Studio, aby znaleźć problematyczny kod.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d59f5b472f791f9774515cdb3e92cc4cf7f9f55b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860740"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilowanie wydajności aplikacji programu SharePoint

Jeśli aplikacje programu SharePoint działają wolno lub nieefektywnie, można użyć funkcji profilowania w programie Visual Studio, aby zidentyfikować problematyczny kod i inne elementy. Korzystając z funkcji testowania obciążeniowego, można określić, jak działa aplikacja programu SharePoint, na przykład gdy wielu użytkowników jednocześnie uzyskuje dostęp do aplikacji. Uruchamiając testy wydajności sieci Web, można mierzyć sposób działania aplikacji w sieci Web. Korzystając z kodowanych testów interfejsu użytkownika, można sprawdzić, czy cała aplikacja programu SharePoint, w tym jej interfejs użytkownika, działa poprawnie. Korzystając ze wszystkich tych testów, mogą one ułatwić zidentyfikowanie problemów z wydajnością przed wdrożeniem aplikacji.

## <a name="profile-tools-overview"></a>Narzędzia profilu — Omówienie

Profilowanie odnosi się do procesu obserwacji i rejestrowania zachowania wydajności aplikacji podczas jej uruchamiania. Przez Profilowanie aplikacji można odkrywać problemy, takie jak wąskie gardła, niewydajny kod i problemy z alokacją pamięci, co powoduje spowolnienie działania aplikacji lub użycie zbyt dużej ilości pamięci. Można na przykład użyć profilowania, aby identyfikować punkty aktywności w kodzie, które są segmentami kodu, które są często nazywane i mogą spowalniać ogólną wydajność aplikacji. Po zidentyfikowaniu punktów aktywnych można je często optymalizować lub wyeliminować.

Aby zidentyfikować i zlokalizować te rodzaje problemów z wydajnością, można użyć kilku narzędzi profilowania w zintegrowanym środowisku programistycznym (IDE). Te narzędzia działają tak samo w przypadku projektów programu SharePoint, jak w przypadku innych rodzajów projektów programu Visual Studio. Kreator wydajności narzędzia profilowania przeprowadzi Cię przez proces tworzenia sesji wydajności, która korzysta z testów określonych przez użytkownika. Sesja wydajności to zbiór danych konfiguracyjnych służący do zbierania informacji o wydajności z aplikacji oraz wyniki jednego lub większej liczby przebiegów profilowania. Sesje wydajności są przechowywane w folderze projektu i można je wyświetlić w **Eksplorator wydajności**. Aby uzyskać więcej informacji, zobacz [Omówienie metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md).

Po utworzeniu i uruchomieniu analizy profilu w aplikacji raport zawiera szczegółowe informacje o jej wydajności. Ten raport może zawierać elementy, takie jak wykres użycia procesora CPU w czasie, stos wywołań funkcji hierarchicznych lub drzewo wywołań. Dokładna zawartość raportu może się różnić w zależności od typu wykonywanego testu, takiego jak próbkowanie lub Instrumentacja. Aby uzyskać więcej informacji, zobacz [Omówienie raportu narzędzia profilowania](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Proces sesji wydajności

Aby profilować aplikację, należy najpierw użyć Kreatora wydajności narzędzia profilowania w celu utworzenia sesji wydajności. Na pasku menu wybierz polecenie **Analizuj**, **Uruchom Kreatora wydajności**. Po zakończeniu pracy kreatora wprowadź wymagane informacje dotyczące sesji wydajności, takie jak wybrana metoda profilu i aplikacja, którą chcesz profilować. Aby uzyskać więcej informacji, zobacz [jak: profilowanie witryny sieci Web lub aplikacji sieci Web za pomocą Kreatora wydajności](../profiling/how-to-collect-performance-data-for-a-web-site.md). Alternatywnie można użyć opcji wiersza polecenia, aby skonfigurować i uruchomić sesję wydajności. Aby uzyskać więcej informacji, zobacz [używanie narzędzia profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md). Jeśli chcesz ręcznie skonfigurować każdy aspekt sesji wydajności, zobacz [jak: ręczne tworzenie sesji wydajności przy użyciu narzędzia profilowania](../profiling/how-to-manually-create-performance-sessions.md). Możesz również utworzyć sesję wydajności na podstawie testu jednostkowego, w oknie **wyniki testów** , otwierając menu skrótów dla testu jednostkowego, a następnie wybierając pozycję **Utwórz sesję wydajności**.

Po skonfigurowaniu sesji wydajności konfiguracja sesji jest zapisywana, serwer jest skonfigurowany do udostępniania danych profilowania, a aplikacja zostanie uruchomiona. Podczas korzystania z aplikacji dane o wydajności są zapisywane w pliku dziennika. Sesje wydajności są wymienione w **Eksplorator wydajności** w folderze **targets** . Po zakończeniu sesji wydajności jego raport zostanie wyświetlony w folderze **raporty** w **Eksplorator wydajności**. Aby wyświetlić raport, otwórz go w **Eksplorator wydajności**. Aby wyświetlić lub skonfigurować właściwości sesji wydajności, otwórz jej menu skrótów w **Eksplorator wydajności**, a następnie wybierz **Właściwości**. Aby uzyskać więcej informacji na temat określonych właściwości sesji wydajności, zobacz [Konfigurowanie sesji wydajności dla narzędzia profilowania](../profiling/configuring-performance-sessions.md). Aby uzyskać informacje na temat interpretacji wyników sesji wydajności, zobacz [analizowanie narzędzia profilowania danych](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Test obciążeniowy

Możesz analizować wydajność aplikacji, tworząc testy obciążeniowe i testy wydajności sieci Web w programie Visual Studio. Podczas tworzenia testu obciążenia w programie Visual Studio należy określić kombinację czynników, zwanych scenariuszem, do testowania aplikacji. Te czynniki obejmują wzorzec obciążenia, model testu mieszanego, mieszany test, mieszanie sieci i mieszane przeglądarki sieci Web. Scenariusze testów obciążenia mogą obejmować zarówno testy jednostkowe, jak i testy wydajności sieci Web.

Rysunek 1. przykład wyników testów obciążenia

![Uruchamianie widoku wykresów testów obciążenia](../sharepoint/media/load-webgraphs.png "Uruchamianie widoku wykresów testów obciążenia")

Testy wydajności sieci Web symulują sposób, w jaki użytkownik końcowy może współdziałać z aplikacją SharePoint. Możesz tworzyć testy wydajności sieci Web, rejestrując żądania HTTP w sesji przeglądarki lub korzystając z **rejestratora testów wydajności sieci Web**. Żądania sieci Web pojawiają się w **Edytor internetowego testu wydajnościowego** po zakończeniu sesji przeglądarki. Następnie można debugować wyniki w **podglądzie wyniki testów wydajności sieci Web**. Możesz również ręcznie tworzyć testy wydajności sieci Web przy użyciu **Edytor internetowego testu wydajnościowego**.

## <a name="test-user-interfaces"></a>Testowanie interfejsów użytkownika

Kodowane testy interfejsu użytkownika automatycznie przełączają aplikację programu SharePoint przy użyciu interfejsu użytkownika. Te testy obejmują kontrolki interfejsu użytkownika, takie jak przyciski i menu, aby sprawdzić, czy działają poprawnie. Ten rodzaj testów jest szczególnie przydatny, jeśli Walidacja lub inna logika jest wykonywana w interfejsie użytkownika, na przykład na stronie sieci Web. Możesz również użyć kodowanych testów interfejsu użytkownika, aby zautomatyzować testy ręczne. Można tworzyć kodowane testy interfejsu użytkownika dla aplikacji programu SharePoint w taki sam sposób, jak w przypadku tworzenia testów dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie aplikacji programu SharePoint 2010 przy użyciu kodowanych testów interfejsu użytkownika](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Profilowanie aplikacji SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Pokazuje, jak przeprowadzić analizę profilu próbkowania w aplikacji SharePoint.|
|[Przetestuj wydajność aplikacji przed wydaniem](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Opisuje sposób tworzenia testów obciążenia, które ułatwiają przetestowanie aplikacji programu SharePoint.|
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Opisuje, jak znaleźć błędy logiki w kodzie przy użyciu testów jednostkowych.|
|[Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|Opisuje sposób testowania interfejsu użytkownika aplikacji programu SharePoint.|

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Podnoszenie jakości kodu](../test/improve-code-quality.md)