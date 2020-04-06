---
title: Szablony pomocy technicznej witryny sieci Web | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703451"
---
# <a name="web-site-support-templates"></a>Szablony pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Szablony projektów i elementów witryny sieci Web zapewniają wielokrotnego użytku i dostosowywalne wycinki projektów i elementów witryny sieci Web, które przyspieszają proces tworzenia, eliminując konieczność tworzenia nowych projektów i elementów witryn sieci Web od podstaw. Aby uzyskać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] więcej informacji na temat szablonów, zobacz [Tworzenie szablonów projektów i elementów](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Folder szablonu projektu
 Szablony projektów sieci Web są zazwyczaj instalowane na [*Ścieżka instalacji programu Visual Studio*]\Common7\IDE\ProjectTemplates\Web\\, każdy w podfolderze, który jest nazwany po języku programowania sieci Web.

## <a name="project-file"></a>Plik projektu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) wymaga rozszerzenia pliku projektu jako sposobu mapowania szablonu do prawidłowego typu projektu. Ponieważ projekty sieci Web nie mają pliku projektu, fikcyjne rozszerzenie pliku projektu .webproj jest rejestrowane w celu mapowania szablonu na typ projektu.

 Opcjonalnie do szablonu można dodać ciąg nazwy języka, aby umożliwić systemowi projektów sieci Web ustawienie domyślnego języka w oknie dialogowym **Dodawanie nowego elementu** dla elementów opartych na szablonie. Ciąg musi być pierwszym wierszem pliku. Musi być zgodna zarówno z nazwą zarejestrowaną w obszarze AddItemLanguageName w rejestracji aparatu IntelliSense, jak i nazwą zarejestrowaną w obszarze Podtyp projektu(VsTemplate). Aby uzyskać więcej informacji, zobacz [Atrybuty pomocy technicznej witryny sieci Web](../../extensibility/internals/web-site-support-attributes.md).

 Jeśli ciąg nie jest obecny, system projektu sieci Web próbuje określić domyślny język na podstawie atrybutu Język i rozszerzeń plików stron dodanych do projektu sieci Web przez szablon projektu.

## <a name="project-templates"></a>Szablony projektów
 Szablony projektów witryn sieci Web są używane do tworzenia nowych witryn sieci Web w odpowiedzi na polecenie **Nowa witryna sieci Web** w menu **Plik.** Obecnie obsługiwane są trzy typy projektów witryny sieci Web:

- Puste projekty witryn sieci Web

- Projekty witryn sieci Web

- Projekty usług sieci Web

### <a name="empty-web-site-projects"></a>Puste projekty witryny sieci Web
 Pliki te tworzą nową pustą witrynę sieci Web w odpowiedzi na polecenie **Pusta witryna sieci Web,** która jest dostępna po **wybraniu opcji Plik** > **nowej witryny sieci Web:**

- EmptyWeb.vstemplate

     Plik szablonu, który prowadzi do tworzenia nowej pustej witryny sieci Web.

- EmptyWeb.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia odwołanie do pliku projektu w pliku EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Projekty witryn sieci Web
 Pliki te tworzą nową witrynę sieci Web w odpowiedzi na **polecenie ASP.NET witryny sieci Web,** które jest dostępne po **wybraniu opcji Plik** > **nowej witryny sieci Web:**

- Default.aspx

     Domyślna strona główna nowej witryny sieci Web. Atrybut Language określa język kodu, a atrybut CodeFile określa plik zależny zawierający kod kodu skojarzonego z tą stroną.

- Default.aspx. *rozszerzenie*

     Plik zależny, który zawiera kodzajęły dla domyślnej strony głównej. Język koduzajdy określa *rozszerzenie* tego pliku.

- Web.config

     Główny plik konfiguracyjny witryny web.site.

- WebApplication.vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza utworzenie folderu App_Data.

- Aplikacja WebApplication.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia odwołanie do pliku projektu w pliku WebApplication.vstemplate.

### <a name="web-service-projects"></a>Projekty usług sieci Web
 Pliki te tworzą nową witrynę sieci Web w odpowiedzi na polecenie **ASP.NET Web Service,** które jest dostępne po **wybraniu opcji Plik** > **nowej witryny sieci Web:**

- Usługa.asmx

     Strona HTML nowej usługi sieci Web. Atrybut Language określa język kodu, a atrybut CodeBehind określa plik zależny zawierający kod kodowy skojarzony z tą usługą.

- Usługi. *Rozszerzenie*

     Plik zależny, który implementuje klasę usługi. Język koduzajdy określa *rozszerzenie* tego pliku.

- Web.config

- Główny plik konfiguracyjny witryny web.site.

- WebService.vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza tworzenie App_Data i App_Code folderów. Usługa. plik *rozszerzenia* jest kopiowany do folderu App_Code.

- Usługa WebService.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia odwołanie do pliku projektu w pliku WebService.vstemplate.

## <a name="project-item-template-folder"></a>Folder szablonu elementu projektu
 Szablony elementów projektu sieci Web są zazwyczaj instalowane w *[Ścieżka instalacji programu*\\Visual Studio ]\Common7\IDE\ItemTemplates\Web , każdy w podfolderze, który jest nazwany po jego języku programowania sieci Web.

## <a name="project-item-templates"></a>Szablony elementów projektu
 Szablony elementów projektu witryny sieci Web służą do dodawania nowych stron sieci Web do witryny sieci Web w odpowiedzi na polecenie **Dodaj istniejący element.** Następujące rodzaje stron sieci Web są obecnie obsługiwane:

- Nowa klasa

- Nowa strona HTML

- Nowy formularz sieci Web

- Nowa strona wzorcowa

### <a name="new-class"></a>Nowa klasa
 Ten szablon tworzy nowy plik źródłowy, który definiuje pustą klasę w odpowiedzi na polecenie **Dodaj nową klasę.**

- Klasa. *Rozszerzenie*

     Plik źródłowy, który implementuje pustą klasę. Język koduzajdy określa *rozszerzenie* tego pliku.

- Płyta class.vstemplate

     Plik szablonu, który tworzy plik źródłowy i określa jego zawartość.

### <a name="new-html-page"></a>Nowa strona HTML
 Ten szablon tworzy nową stronę sieci Web w odpowiedzi na polecenie **Dodaj nową stronę HTML.**

- Strona HTML.htm

     Początkowa zawartość strony sieci Web. Ta strona sieci Web zazwyczaj nie ma skojarzonego pliku zależnego od kodu. Aby utworzyć stronę inteligentną ze skojarzonym plikiem kodu za nim, użyj szablonu formularza sieci Web.

- Płyta HTMLPage.vstemplate

     Plik szablonu, który tworzy stronę sieci Web i określa jej zawartość.

### <a name="new-webform"></a>Nowy webform
 Ten szablon tworzy nową inteligentną stronę sieci Web w odpowiedzi na polecenie **Dodaj nowy formularz sieci Web.**

 Aby utworzyć zależny plik źródłowy kodu, wybierz **opcję Umieść kod w osobnym pliku**. W przeciwnym razie tworzona jest pojedyncza strona \<sieci Web, która ma pusty blok skryptów i nie ma % Page %> dyrektyw, aby podłączyć plik zależny.

 Aby utworzyć stronę zawartości dla wybranej strony wzorcowej, wybierz pozycję **Wybierz stronę wzorcową**.

- WebForm.aspx

     Początkowa zawartość strony sieci Web. Ta strona sieci Web nie ma skojarzonego pliku zależnego od kodu.

- WebForm_cb.aspx

     Początkowa zawartość strony sieci Web. Ta strona sieci Web ma skojarzony plik zależny od koduza pomocą.

- Codebehind. *Rozszerzenie*

     Plik zależny, który implementuje klasę webform. Język koduzajdy określa *rozszerzenie* tego pliku.

- Strona ContentPage.aspx

     Początkowa zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web nie ma skojarzonego pliku zależnego od kodu.

- ContentPage_cb.aspx

     Początkowa zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web ma skojarzony plik zależny od koduza pomocą.

- WebForm.vstemplate

     Plik szablonu, który określa zawartość nowej strony sieci web i jej pliku zależnego, jeśli istnieje.

### <a name="new-master-page"></a>Nowa strona wzorcowa
 Ten szablon tworzy nową stronę wzorcową w odpowiedzi na polecenie **Dodaj nową stronę wzorcową.**

 Aby utworzyć zależny plik źródłowy kodu, wybierz **opcję Umieść kod w osobnym pliku**. W przeciwnym razie tworzona jest pojedyncza strona \<sieci Web, która ma pusty blok skryptów i nie ma % Page %> dyrektyw, aby podłączyć plik zależny.

- MasterPage.master

     Początkowa zawartość strony wzorcowej. Ta strona wzorcowa nie ma skojarzonego pliku zależnego od kodu.

- MasterPage_cb.master

     Początkowa zawartość strony wzorcowej. Ta strona wzorcowa ma skojarzony plik zależny od koduzagod.

- Codebehind. *rozszerzenie*

     Plik zależny, który implementuje klasę strony wzorcowej. Język koduzajdy określa *rozszerzenie* tego pliku.

- Płyta MasterPage.vstemplate

     Plik szablonu, który określa zawartość nowej strony wzorcowej i jej pliku zależnego, jeśli istnieje.

## <a name="see-also"></a>Zobacz też
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
