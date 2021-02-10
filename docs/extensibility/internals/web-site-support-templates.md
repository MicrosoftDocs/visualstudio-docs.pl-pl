---
title: Szablony obsługi witryny sieci Web | Microsoft Docs
description: Dowiedz się więcej o szablonach pomocy technicznej witryny sieci Web. Szablony projektów i elementów witryny sieci Web programu Visual Studio zapewniają wielokrotny i Dostosowywalny projekt witryny sieci Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 988b81e72ff7714cb8a0983655de551b54c9150c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940036"
---
# <a name="web-site-support-templates"></a>Szablony pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Szablony projektów i elementów witryny sieci Web zapewniają możliwość wielokrotnego użytku i dostosowywania projektu witryny sieci Web oraz elementów, które przyspieszają proces opracowywania, usuwając konieczność tworzenia nowych projektów i danych witryn sieci Web od podstaw. Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablonów, zobacz [Tworzenie szablonów projektów i elementów](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Folder szablonu projektu
 Szablony projektu sieci Web są zazwyczaj instalowane na [*ścieżka instalacji programu Visual Studio*] \Common7\IDE\ProjectTemplates\Web \\ , z których każdy znajduje się w podfolderze o nazwie zgodnej z językiem programowania sieci Web.

## <a name="project-file"></a>Plik projektu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE) wymaga rozszerzenia pliku projektu jako metody mapowania szablonu na właściwy typ projektu. Ponieważ projekty sieci Web nie mają pliku projektu, rozszerzenie pliku projektu fikcyjnego jest zarejestrowane w celu zamapowania szablonu na typ projektu.

 Opcjonalnie można dodać ciąg nazwy języka do szablonu, aby umożliwić systemowi projektu sieci Web ustawienie języka domyślnego w oknie dialogowym **Dodaj nowy element** dla elementów opartych na szablonie. Ciąg musi być pierwszym wierszem pliku. Musi pasować zarówno do nazwy zarejestrowanej w AddItemLanguageName w ramach rejestracji aparatu IntelliSense, jak i nazwy zarejestrowanej pod podtypem projektu (VsTemplate). Aby uzyskać więcej informacji, zobacz [atrybuty obsługi witryny sieci Web](../../extensibility/internals/web-site-support-attributes.md).

 Jeśli ciąg nie jest obecny, system projektu sieci Web próbuje określić domyślny język na podstawie atrybutów języka i rozszerzeń plików stron dodanych do projektu sieci Web według szablonu projektu.

## <a name="project-templates"></a>Szablony projektów
 Szablony projektu witryny sieci Web służą do tworzenia nowych witryn sieci Web w odpowiedzi na **nową witrynę sieci Web** w menu **plik** . Obecnie obsługiwane są trzy typy projektów witryny sieci Web:

- Puste projekty witryny sieci Web

- Projekty witryny sieci Web

- Projekty usługi sieci Web

### <a name="empty-web-site-projects"></a>Puste projekty witryny sieci Web
 Te pliki tworzą nową pustą witrynę sieci Web w odpowiedzi na **pustą witrynę sieci Web** , która jest dostępna po wybraniu opcji **plik**  >  **Nowa witryna sieci Web**:

- EmptyWeb. vstemplate

     Plik szablonu, który prowadzi do tworzenia nowej pustej witryny sieci Web.

- EmptyWeb. webproj

     Ten plik jest artefaktem systemu szablonu projektu. Jest on zgodny z odwołaniem do pliku projektu w pliku EmptyWeb. vstemplate.

### <a name="web-site-projects"></a>Projekty witryny sieci Web
 Te pliki tworzą nową witrynę sieci Web w odpowiedzi na polecenie **ASP.NET Web site** , które jest dostępne po wybraniu opcji **plik**  >  **Nowa witryna sieci Web**:

- Default.aspx

     Domyślna strona główna nowej witryny sieci Web. Atrybut Language określa język CodeBehind, a atrybut atrybutu 'codefile określa plik zależny, który zawiera kod CodeBehind skojarzony z tą stroną.

- Default. aspx. *rozszerzenie*

     Plik zależny zawierający kod CodeBehind dla domyślnej strony głównej. Język CodeBehind określa *rozszerzenie* tego pliku.

- web.config

     Główny plik konfiguracji Web. site.

- WebApplication. vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza tworzenie folderu App_Data.

- WebApplication. webproj

     Ten plik jest artefaktem systemu szablonu projektu. Jest on zgodny z odwołaniem do pliku projektu w pliku WebApplication. vstemplate.

### <a name="web-service-projects"></a>Projekty usługi sieci Web
 Te pliki tworzą nową witrynę sieci Web w odpowiedzi na polecenie **usługi sieci Web ASP.NET** , która jest dostępna po wybraniu opcji **plik**  >  **Nowa witryna sieci Web**:

- Usługa. asmx

     Strona HTML nowej usługi sieci Web. Atrybut Language określa język CodeBehind, a atrybut CodeBehind określa plik zależny, który zawiera kod CodeBehind skojarzony z tą usługą.

- Usługi. *rozszerzenia*

     Plik zależny, który implementuje klasę usługi. Język CodeBehind określa *rozszerzenie* tego pliku.

- web.config

- Główny plik konfiguracji Web. site.

- Usługa WebService. vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza tworzenie App_Data i App_Code folderów. Usługa. plik *rozszerzenia* jest kopiowany do folderu App_Code.

- Usługa WebService. webproj

     Ten plik jest artefaktem systemu szablonu projektu. Jest on zgodny z odwołaniem do pliku projektu w pliku WebService. vstemplate.

## <a name="project-item-template-folder"></a>Folder szablonu elementu projektu
 Szablony elementów projektu sieci Web są zazwyczaj instalowane w [*ścieżka instalacji programu Visual Studio*] \Common7\IDE\ItemTemplates\Web \\ , każdy w podfolderze o nazwie po jego języku programowania sieci Web.

## <a name="project-item-templates"></a>Szablony elementów projektu
 Szablony elementów projektu witryny sieci Web służą do dodawania nowych stron sieci Web do witryny sieci Web w odpowiedzi na polecenie **Dodaj istniejący element** . Te rodzaje stron sieci Web są obecnie obsługiwane:

- Nowa klasa

- Nowa strona HTML

- Nowy formularz sieci Web

- Nowa Strona główna

### <a name="new-class"></a>Nowa klasa
 Ten szablon służy do tworzenia nowego pliku źródłowego, który definiuje pustą klasę w odpowiedzi na polecenie **Dodaj nową klasę** .

- Określonej. *rozszerzenia*

     Plik źródłowy, który implementuje pustą klasę. Język CodeBehind określa *rozszerzenie* tego pliku.

- Klasa. vstemplate

     Plik szablonu, który tworzy plik źródłowy i określa jego zawartość.

### <a name="new-html-page"></a>Nowa strona HTML
 Ten szablon służy do tworzenia nowej strony sieci Web w odpowiedzi na polecenie **Dodaj nową stronę HTML** .

- HTMLPage.htm

     Początkowa zawartość strony sieci Web. Ta strona sieci Web zwykle nie ma skojarzonego pliku zależnego od Codebehind. Aby utworzyć stronę inteligentną z skojarzonym plikiem CodeBehind, użyj szablonu formularza sieci Web.

- HTMLPage. vstemplate

     Plik szablonu, który tworzy stronę sieci Web i określa jej zawartość.

### <a name="new-webform"></a>Nowy formularz WebForm
 Ten szablon służy do tworzenia nowej inteligentnej strony sieci Web w odpowiedzi na polecenie **Dodaj nowy formularz sieci Web** .

 Aby utworzyć zależny plik źródłowy CodeBehind, wybierz pozycję **Umieść kod w osobnym pliku**. W przeciwnym razie zostanie utworzona jedna strona sieci Web, która ma pusty blok skryptu i nie ma żadnych \<% Page %> dyrektyw, aby podłączyć plik zależny.

 Aby utworzyć stronę zawartości dla wybranej strony głównej, wybierz pozycję **Wybierz stronę wzorcową**.

- WebForm. aspx

     Początkowa zawartość strony sieci Web. Ta strona sieci Web nie ma skojarzonego pliku zależnego od Codebehind.

- WebForm_cb. aspx

     Początkowa zawartość strony sieci Web. Ta strona sieci Web zawiera skojarzony plik zależny od Codebehind.

- CodeBehind. *rozszerzenia*

     Plik zależny, który implementuje klasę WebForm. Język CodeBehind określa *rozszerzenie* tego pliku.

- ContentPage. aspx

     Początkowa zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web nie ma skojarzonego pliku zależnego od Codebehind.

- ContentPage_cb. aspx

     Początkowa zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web zawiera skojarzony plik zależny od Codebehind.

- WebForm. vstemplate

     Plik szablonu, który określa zawartość nowej strony sieci Web i jej pliku zależnego, jeśli istnieje.

### <a name="new-master-page"></a>Nowa Strona główna
 Ten szablon służy do tworzenia nowej strony wzorcowej w odpowiedzi na polecenie **Dodaj nową stronę wzorcową** .

 Aby utworzyć zależny plik źródłowy CodeBehind, wybierz pozycję **Umieść kod w osobnym pliku**. W przeciwnym razie zostanie utworzona jedna strona sieci Web, która ma pusty blok skryptu i nie ma żadnych \<% Page %> dyrektyw, aby podłączyć plik zależny.

- MasterPage. Master

     Początkowa zawartość strony głównej. Ta strona wzorcowa nie ma skojarzonego pliku zależnego od Codebehind.

- MasterPage_cb. Master

     Początkowa zawartość strony głównej. Ta strona wzorcowa ma skojarzony plik zależny Codebehind.

- CodeBehind. *rozszerzenie*

     Plik zależny, który implementuje klasę strony głównej. Język CodeBehind określa *rozszerzenie* tego pliku.

- MasterPage. vstemplate

     Plik szablonu, który określa zawartość nowej strony wzorcowej i jej pliku zależnego, jeśli istnieje.

## <a name="see-also"></a>Zobacz też
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
