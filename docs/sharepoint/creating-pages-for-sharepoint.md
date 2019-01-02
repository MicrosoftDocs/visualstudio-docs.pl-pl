---
title: Tworzenie stron dla SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71f0a75678c0123853f128f42bfdbf1c75ac0c74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859818"
---
# <a name="create-pages-for-sharepoint"></a>Tworzenie stron dla SharePoint
  W programie SharePointmMożna utworzyć strony aplikacji, strony w witrynie, strony wzorcowe i układy stron witryny programu SharePoint.  
  
 Strony aplikacji można tworzyć za pomocą szablonu w programie Visual Studio. Tworzenie stron w witrynie, stron wzorcowych i układów stron jest możliwe za pomocą programu SharePoint Designer. Następnie można zaimportować te strony do programu Visual Studio, aby korzystać z nich w projekcie programu SharePoint.  
  
 Przy użyciu kaskadowych arkuszy stylów, ECMAScript i motywów, można zmodyfikować wygląd i zachowanie stron.  
  
## <a name="types-of-sharepoint-pages"></a>Typy stron programu SharePoint
 W poniższej tabeli opisano cztery główne typy stron, które zawiera witryny programu SharePoint.  
  
|Typ strony|Opis|  
|---------------|-----------------|  
|Strony aplikacji|Utwórz stronę aplikacji, jeśli strona ma zawierać kod niestandardowy lub ma być udostępniana w wielu lokacjach. W przeciwnym razie strona witryny może być najlepszym rozwiązaniem.|  
|Strony witryny|Utwórz stronę witryny, jeśli chcesz wykonać jedno z następujących zadań:<br /><br /> — Dodanie strony do biblioteki programu SharePoint.<br />— Umożliwienie stronie hostowania funkcji, takich jak dynamiczne składniki Web Part i strefy składników Web Part.<br />— Umożliwienie użytkownikom dostosowywania strony przy użyciu programu SharePoint Designer.<br /><br /> Nie należy tworzyć strony witryny, jeśli strona ma zawierać kod niestandardowy. Mimo że można dodać kod niestandardowy do strony witryny, kod przestanie działać, kiedy użytkownik dostosuje stronę za pomocą programu SharePoint Designer.|  
|Strony wzorcowe|Utwórz stronę wzorcową, jeśli chcesz zdefiniować strukturę typowe dla stron witryny i stron aplikacji.|  
|Układy stron|Układy stron są specyficzne dla [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] i umożliwiają uściślić wspólnej struktury stron witryny i stron aplikacji.|  
  
 Omówienie każdego typu strony, zobacz [bloków konstrukcyjnych: Strony i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095), i [układów strony i stronami wzorcowymi](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="create-application-pages"></a>Tworzenie stron aplikacji
 W programie Visual Studio można utworzyć strony aplikacji, dodając **strony aplikacji** elementu do projektu programu SharePoint. Można dodać formanty do strony, a następnie obsługiwać zdarzenia formantu przez dodanie kodu.  
  
 Możesz ustawić punkty przerwania w pliku kodu strony, uruchom debuger i przetestować bez wykonywania dodatkowych czynności konfiguracyjnych na lokalnej witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="create-site-pages-master-pages-and-page-layouts"></a>Tworzenie stron witryny, strony wzorcowe i układy stron
 Można utworzyć strony witryny, strony wzorcowe i układy stron przy użyciu programu SharePoint Designer. Następnie można zaimportować te strony w programie Visual Studio. Importuj strony, jeśli chcesz korzystać z zalet wdrażania lub funkcji kontroli źródła, które są dostępne w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Ponieważ trudno jest modyfikować te strony po zaimportowaniu, należy je projektować przed zaimportowaniem.  
  
## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Tworzenie kaskadowych arkuszy stylów, ECMAScript i motywów
 Program Visual Studio nie zapewnia szablony dla opracowywania kaskadowych arkuszy stylów (CSS), ECMAScript (JavaScript i JScript) lub pliki motywów witryny programu SharePoint. Pliki te można utworzyć, korzystając ze wskazówek dostępnych w zestawie SDK programu SharePoint lub za pomocą narzędzi, takich jak SharePoint Designer.  
  
 Te pliki można dodać bezpośrednio do rozwiązania, lub można je zaimportować. W obu przypadkach należy utworzyć odpowiednie folderów mapowanych dla każdego elementu, który dodajesz. Aby uzyskać więcej informacji na temat tworzenia zamapowany folder, zobacz [porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia kaskadowe arkusze stylów, zobacz [Cascading Style arkusze klasy użycia w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Aby uzyskać więcej informacji o tworzeniu plików JavaScript i JScript dla rozwiązania programu SharePoint, zobacz [ustawienie zapasowej podstawowy strony ASPX dla ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Aby uzyskać więcej informacji o motywach, zobacz [bloków konstrukcyjnych: Strony i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|W tym artykule opisano sposób dodawania strony aplikacji: *.aspx* zawartość, która jest połączone ze stroną wzorcową programu SharePoint.|  
|[Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)|Dowiesz się, jak utworzyć strony ASP.NET, które są uruchamiane w witrynie programu SharePoint.|  
|[Przewodnik: Tworzenie strony aplikacji SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Pokazuje, jak projektować i debugowania na stronie sieci Web platformy ASP.NET dla witryny programu SharePoint.|  
