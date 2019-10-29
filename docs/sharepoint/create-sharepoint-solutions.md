---
title: Tworzenie rozwiązań SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1e5be38d0d44912052466162abaaa496c608d27
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981298"
---
# <a name="create-sharepoint-solutions"></a>Tworzenie rozwiązań SharePoint
  Możesz tworzyć aplikacje programu SharePoint w programie Visual Studio jako alternatywę do tworzenia ich w programie SharePoint Designer. Program Visual Studio promuje szybkie programowanie SharePoint, dostarczając takie funkcje jak zaawansowane narzędzia do debugowania, IntelliSense, Uzupełnianie składni i szablony projektów. Program Visual Studio korzysta również z zaawansowanych narzędzi i języków opartych na .NET Framework. Możesz tworzyć projekty programu SharePoint za pomocą Visual Basic lub wizualizacji C#, a także tworzyć aplikacje dla projektów programu SharePoint przy użyciu języka JavaScript.

 Aby uzyskać informacje na temat dodatków SharePoint 2013 i SharePoint, zobacz [sharepoint 2013](https://products.office.com/previous-versions/microsoft-sharepoint-2013) i [Build Apps for SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

> [!NOTE]
> Dowiedz się, jak korzystać z nowego [modelu dodatku programu SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) , aby zwiększyć możliwości programu SharePoint dla użytkowników. Te dodatki mają bardzo małe rozmiary w porównaniu z rozwiązaniami programu SharePoint i można je skompilować przy użyciu prawie dowolnej technologii programowania sieci Web, takiej jak HTML5, JavaScript, CSS3 i XML.

|||
|-|-|
|![Dokumentacja](../sharepoint/media/vs-icon-documentation.gif "Dokumentacja")|**Dokumentacja**<br /><br /> -   [ &#40;wprowadzenie do programowania SharePoint w programie Visual&#41; Studio](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)<br />-   [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [kompilowania i debugowania rozwiązań programu SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|
|![Dokumentacja](../sharepoint/media/vs-icon-documentation.gif "Dokumentacja")|**Polecane zadania**<br /><br /> [przewodnik -   : Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [jak utworzyć odbiorcę zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [jak utworzyć model usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [: Tworzenie składnika Web Part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [instrukcje: Tworzenie kontrolki użytkownika dla strony aplikacji lub składnika sieci Web programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![Przewodniki](../sharepoint/media/vs-icon-walkthroughs.gif "Wskazówki")|**Przewodniki**<br /><br /> -   [Instruktaże dotyczące projektowania programu SharePoint](../sharepoint/sharepoint-development-walkthroughs.md)|
|![Przykłady kodu](../sharepoint/media/vs-icon-codesamples.gif "Przykłady kodu")|**Przykłady kodu**<br /><br /> [przykłady projektowania programu SharePoint](../sharepoint/sharepoint-development-samples.md) -   <br />-   [do pobrania dla deweloperów programu SharePoint](/sharepoint/dev/)|
|![Szkolącej](../sharepoint/media/vs-icon-training.gif "Szkolącej")|**Szkolącej**<br /><br /> -   [uczyć się projektowania programu SharePoint](/sharepoint/dev/)|
|![Dotyczące](../sharepoint/media/vs-icon-forums.gif "Fora")|**Dotyczące**<br /><br /> -   [programowanie SharePoint przy użyciu programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment)<br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![Szkolącej](../sharepoint/media/vs-icon-training.gif "Szkolącej")|**Blogi**<br /><br /> Blog dotyczący [tworzenia -   Visual Studio SharePoint](https://blogs.msdn.microsoft.com/vssharepointtoolsblog/)|
|![Jak to zrobić? Wideo](../sharepoint/media/vs-icon-howdoivideos.gif "Jak to zrobić? Wideo")|**Jak to zrobić? Wideo**<br /><br /> -   [jak: Tworzenie visual składniki Web Part dla programu SharePoint 2010 w programie Visual Studio 2010?](https://visualstudio.microsoft.com/)<br />-   [jak: Tworzenie typów zawartości dla programu SharePoint 2010 w programie Visual Studio 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [jak: Tworzenie definicji witryny dla programu SharePoint 2010 w programie Visual Studio 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [jak: utworzyć model łączności danych firmy dla programu SharePoint 2010 przy użyciu programu Visual Studio 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Wideo Channel 9](../sharepoint/media/vs-icon-channel9videos.gif "Wideo Channel 9")|**Wideo Channel 9**<br /><br /> -   [Omówienie programowania SharePoint w programie Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010)<br />-   [najlepszych praktyk dotyczących kompilowania składniki Web Part programu SharePoint 2010 w programie Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010)<br />-   [funkcji programu SharePoint i projektantów pakietów w programie Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010)|
|![Centrum deweloperów](../sharepoint/media/vs-icon-msdndevcenter.gif "Centrum deweloperów")|**Centra deweloperów**<br /><br /> -   [centrum deweloperskie programu Visual Studio](https://visualstudio.microsoft.com/)<br />-   [Centrum deweloperów programu SharePoint](/sharepoint/dev/)<br />-   [Centrum deweloperów programu SharePoint Server](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [Centrum deweloperów programu SharePoint Designer](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [Centrum deweloperów ASP.NET](https://msdn.microsoft.com/aa336522.aspx)|
|![Przekazywanie opinii](../sharepoint/media/vs-icon-feedback.gif "Przekazywanie opinii")|**Przekazywanie opinii**<br /><br /> Prześlij opinię na temat programu Visual Studio:<br /><br /> -   [Microsoft Connect](/collaborate/connect-redirect)<br /><br /> Prześlij opinię na temat dokumentacji programu Visual Studio:<br /><br /> **Widok lekki -   .** Jeśli jesteś w górnej części dowolnego tematu, możesz wybrać łącze **Oceń ten temat** , aby przejść do dolnej części tego tematu, gdzie można określić **tak** lub **nie** w odpowiedzi na to, czy chcesz **to ułatwić?** Następnie można wybrać jedno lub więcej pól wyboru, które są wyświetlane, jeśli wybrano opcję **nie**, podać więcej informacji w polu tekstowym lub w obu tych polach. Po zakończeniu wybierz przycisk **Prześlij** .<br />-   **Widok Scriptfree.** W górnej części tematu wybierz link **opinii** , aby przekazać opinię na forum opinii w witrynie TechNet i Expression Library.<br />-   **widoku klasycznym.** W górnej części tematu wybierz ikony **kliknij, aby ocenić i przesłać opinię** , aby przesłać opinię na temat tematu do zespołu dokumentacji.|
