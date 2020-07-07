---
title: Tworzenie stron dla programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015163"
---
# <a name="create-pages-for-sharepoint"></a>Tworzenie stron dla programu SharePoint
  Można tworzyć strony aplikacji, strony witryny, strony wzorcowe i układy stron dla witryny programu SharePoint.

 Możesz tworzyć strony aplikacji przy użyciu szablonu w programie Visual Studio. Tworzenie stron lokacji, stron wzorcowych i układów stron przy użyciu programu SharePoint Designer. Następnie można zaimportować te strony do programu Visual Studio, aby użyć ich w projekcie programu SharePoint.

 Możesz również modyfikować wygląd i zachowanie stron przy użyciu kaskadowych arkuszy stylów, ECMAScript i motywów.

## <a name="types-of-sharepoint-pages"></a>Typy stron programu SharePoint
 W poniższej tabeli opisano cztery główne typy stron, które zawiera witryna programu SharePoint.

|Typ strony|Opis|
|---------------|-----------------|
|Strony aplikacji|Utwórz stronę aplikacji, jeśli chcesz, aby strona zawierała kod niestandardowy, lub chcesz, aby strona była współdzielona między wieloma lokacjami. W przeciwnym razie na stronie witryny może być najlepszym wyborem.|
|Strony witryny|Utwórz stronę witryny, jeśli chcesz wykonać dowolne z następujących zadań:<br /><br /> -Dodaj stronę do biblioteki programu SharePoint.<br />-Włącz funkcję hostowania funkcji, takich jak dynamiczne składniki Web Part i strefy składników Web Part.<br />— Umożliwia użytkownikom Dostosowywanie strony przy użyciu programu SharePoint Designer.<br /><br /> Nie twórz strony witryny, jeśli chcesz, aby strona zawierała kod niestandardowy. Mimo że można dodać niestandardowy kod do strony witryny, kod przestaje działać, gdy użytkownik dostosowuje stronę przy użyciu programu SharePoint Designer.|
|Strony wzorcowe|Utwórz stronę wzorcową, jeśli chcesz zdefiniować strukturę wspólną dla stron witryny i stron aplikacji.|
|Układy stron|Układy stron są specyficzne dla programu [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] i umożliwiają dokładniejsze zdefiniowanie wspólnej struktury stron witryny i stron aplikacji.|

 Aby zapoznać się z omówieniem każdego typu strony, zobacz [blok konstrukcyjny: strony i interfejs użytkownika](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))oraz [układów stron i stron wzorcowych](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Tworzenie stron aplikacji
 W programie Visual Studio można tworzyć strony aplikacji, dodając element **strony aplikacji** do projektu programu SharePoint. Można dodać kontrolki do strony, a następnie obsłużyć zdarzenia sterujące przez dodanie kodu.

 Można ustawić punkty przerwania w pliku kodu strony, uruchomić debuger i przetestować stronę w lokalnej witrynie programu SharePoint bez konieczności wykonywania dodatkowych czynności konfiguracyjnych. Aby uzyskać więcej informacji, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Tworzenie stron witryny, stron wzorcowych i układów stron
 Za pomocą programu SharePoint Designer można tworzyć strony witryny, strony wzorcowe i układy stron. Następnie można zaimportować te strony do programu Visual Studio. Zaimportuj strony, jeśli chcesz skorzystać z funkcji wdrożenia lub kontroli źródła, które są dostępne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Ze względu na to, że te strony trudno modyfikować po ich zaimportowaniu, należy zaprojektować te strony przed ich zaimportowaniem.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Tworzenie kaskadowych arkuszy stylów, ECMAScript i motywów
 Program Visual Studio nie udostępnia szablonów do tworzenia kaskadowe arkusze stylów (CSS), ECMAScript (JavaScript, JScript) ani plików motywów dla witryn programu SharePoint. Te pliki można utworzyć przy użyciu wskazówek dostępnych w zestawie SDK programu SharePoint lub przy użyciu narzędzi, takich jak SharePoint Designer.

 Te pliki można dodać do rozwiązania bezpośrednio lub można je zaimportować. W obu przypadkach należy utworzyć odpowiednie zamapowane foldery dla każdego dodawanego elementu. Aby uzyskać więcej informacji na temat sposobu tworzenia zamapowanego folderu, zobacz [How to: Add i Remove zamapowany](../sharepoint/how-to-add-and-remove-mapped-folders.md)Folders.

 Aby uzyskać więcej informacji na temat tworzenia kaskadowe arkusze stylów, zobacz [kaskadowe arkusze stylów klasy użycie w programie SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Aby uzyskać więcej informacji na temat tworzenia plików JavaScript i JScript dla rozwiązania SharePoint, zobacz [Konfigurowanie podstawowej strony aspx dla języka ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Aby uzyskać więcej informacji na temat motywów, zobacz [Building Block: Pages and the User Interface](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Opisuje sposób dodawania stron aplikacji: zawartość *. aspx* Scalonej ze stroną wzorcową programu SharePoint.|
|[Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)|Pokazuje, jak utworzyć strony ASP.NET, które działają w witrynie programu SharePoint.|
|[Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Pokazuje, jak projektować i debugować stronę sieci Web ASP.NET dla witryny programu SharePoint.|
