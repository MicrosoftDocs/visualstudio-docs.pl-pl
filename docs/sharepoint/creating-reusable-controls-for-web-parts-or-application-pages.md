---
title: Tworzenie kontrolek wielokrotnego użytku dla składniki Web Part lub stron aplikacji | Microsoft Docs
titleSuffix: ''
description: Tworzenie niestandardowych kontrolek wielokrotnego użytku (kontrolki użytkownika) w programie Visual Studio, które mogą być używane przez strony aplikacji i składniki Web Part, które są uruchamiane w programie SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b61474f4290771fb139d511296580ec1ef0f8820
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213917"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji
  W programie Visual Studio można tworzyć niestandardowe kontrolki wielokrotnego użytku, które mogą być używane przez strony aplikacji oraz składniki Web Part, które są uruchamiane w programie SharePoint. Formanty te są nazywane kontrolkami użytkownika. Kontrolka użytkownika to rodzaj kontrolki złożonej, który działa podobnie jak strona sieci Web ASP.NET — można dodać istniejące kontrolki serwera sieci Web i znaczniki do kontrolki użytkownika, a także zdefiniować właściwości i metody dla kontrolki. Następnie można je osadzić na stronach sieci Web ASP.NET, gdzie działają jako jednostka.

## <a name="create-a-user-control"></a>Tworzenie kontrolki użytkownika
 Aby utworzyć kontrolkę użytkownika, Dodaj **kontrolkę użytkownika** do **pustego projektu programu SharePoint**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie kontrolki użytkownika dla strony aplikacji SharePoint lub składnika Web Part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Po dodaniu elementu **kontrolki użytkownika** program Visual Studio tworzy folder w projekcie, a następnie dodaje kilka plików do tego folderu. W poniższej tabeli opisano każdy plik.

|Plik|Opis|
|----------|-----------------|
|Plik kontrolny użytkownika|Definiuje kontrolkę użytkownika. Zaprojektuj kontrolkę użytkownika, dodając kontrolki i adiustację do tego pliku.|
|Plik kodu|Zawiera kod związany z kontrolką użytkownika. Dodaj kod obsługujący zdarzenia do tego pliku.|
|Plik kodu projektanta|Zawiera kod generowany przez projektanta i nie powinien być edytowany bezpośrednio.|

## <a name="design-the-user-control"></a>Projektowanie kontrolki użytkownika
 Zaprojektuj kontrolkę użytkownika przy użyciu projektanta Visual Web Developer w programie Visual Studio. Ten projektant pojawia się po otwarciu pliku kontrolnego użytkownika w projekcie i wybraniu karty **projekt** .

## <a name="consume-the-user-control"></a>Korzystanie z kontrolki użytkownika
 Kontrolki użytkownika nie są wyświetlane w programie SharePoint, dopóki nie zostaną uwzględnione na stronie aplikacji lub składniku Web Part.

 Aby dołączyć kontrolkę użytkownika na stronie aplikacji, Otwórz stronę sieci Web, do której chcesz dodać kontrolkę użytkownika ASP.NET. Przejdź do widok Projekt, a następnie wybierz niestandardowy plik kontrolki użytkownika w Eksplorator rozwiązań i przeciągnij go na stronę. Kontrolka użytkownika ASP.NET jest dodawana do strony, a projektant tworzy dyrektywę @ Register, która jest wymagana dla strony do rozpoznawania kontrolki użytkownika. Teraz możesz współpracować z publicznymi właściwościami i metodami kontrolki.

 Aby dołączyć kontrolkę użytkownika do składnika Web Part, Dodaj kontrolkę użytkownika do kolekcji składników Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> w pliku kodu składnika Web Part. Poniższy przykład dodaje kontrolkę użytkownika do <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> kolekcji części sieci Web.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs" id="Snippet5":::

## <a name="debug-a-user-control"></a>Debugowanie kontrolki użytkownika
 Aby debugować kontrolkę użytkownika, upewnij się, że kontrolka użytkownika jest uwzględniona na stronie aplikacji lub składniku Web Part w projekcie programu SharePoint. Następnie można debugować kod w kontrolce użytkownika tak samo jak w przypadku debugowania kodu w dowolnym projekcie programu Visual Studio.

 Po uruchomieniu debugera programu Visual Studio program Visual Studio otwiera witrynę programu SharePoint.

 W programie SharePoint otwórz stronę aplikacji, która zawiera kontrolkę użytkownika. Jeśli kontrolka użytkownika jest uwzględniona w składniku Web Part, należy dodać składnik Web Part do strony składnika Web Part w programie SharePoint.

 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Tworzenie kontrolki użytkownika dla strony aplikacji lub składnika sieci Web programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Pokazuje, jak utworzyć niestandardowe kontrolki do wielokrotnego użytku, które mogą być używane przez strony aplikacji oraz składniki Web Part, które są uruchamiane w programie SharePoint.|
