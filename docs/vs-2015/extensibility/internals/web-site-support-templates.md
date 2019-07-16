---
title: Szablony pomocy technicznej dotyczącej witryn sieci Web | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca7768f31219328648d457d188086e0185e2ffc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200965"
---
# <a name="web-site-support-templates"></a>Szablony pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Szablony projektów i elementów dla witryn sieci Web zawierają wycinków projektów i elementów witryny sieci Web wielokrotnego użytku i można go dostosowywać, przyspieszające proces tworzenia aplikacji, usuwając konieczność do utworzenia nowych projektów witryny sieci Web i elementy od początku. Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] szablonów, zobacz [tworzenie projektów i szablonów elementów](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Folder szablonu projektu  
 Szablony szablon projektów internetowych są instalowane w [*ścieżkę instalacji w usłudze Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, każdy w podfolderze o nazwie po język programowania sieci web.  
  
## <a name="project-file"></a>Plik projektu  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) wymaga rozszerzenia pliku projektu jako sposób mapowania szablonu do typu właściwy projekt. Ponieważ projekty sieci Web nie ma pliku projektu, .webproj rozszerzenie pliku projektu zastępczy jest zarejestrowany w tym.  
  
 Opcjonalnie, ciąg nazwy języka można dodać do szablonu, aby włączyć system projektu sieci Web, aby ustawić język domyślny w **Dodaj nowy element** okno dialogowe dla elementów na podstawie szablonu. Ciąg musi być pierwszym wierszem pliku i musi odpowiadać zarówno nazwę zarejestrowany pod AddItemLanguageName w rejestracji aparatu funkcji Intellisense, jak i nazwę zarejestrowany pod Subtype(VsTemplate) projektu. Aby uzyskać więcej informacji, zobacz [witryny sieci Web pomocy technicznej atrybuty](../../extensibility/internals/web-site-support-attributes.md).  
  
 Jeśli ciąg nie jest obecny, system projektu sieci Web spróbuje określić domyślny język na podstawie rozszerzeń atrybut i plik języka strony dodane do projektu sieci Web przez szablon projektu szablon.  
  
## <a name="project-templates"></a>Szablony projektów  
 Szablony projektów witryny sieci Web są używane do tworzenia nowych witryn sieci Web w odpowiedzi na **nową witrynę sieci Web** polecenie **pliku** menu. Obecnie obsługiwane są trzy typy projektu witryny sieci Web:  
  
- Pusta witryna internetowa projektów  
  
- Projektów witryny sieci Web  
  
- Projekty usługi w sieci Web  
  
### <a name="empty-web-site-projects"></a>Pusta witryna internetowa projektów  
 Te pliki, Utwórz kopię zapasową witryny sieci Web w odpowiedzi na **pusta witryna internetowa** polecenia, które jest dostępne po wskazaniu **nową witrynę sieci Web** na **pliku** menu:  
  
- EmptyWeb.vstemplate  
  
     Plik szablonu, który zawiera informacje na temat tworzenia nowych pusta witryna sieci Web.  
  
- EmptyWeb.webproj  
  
     Ten plik jest pozostałością system szablonu projektu. Spełnia odwołanie do pliku projektu w pliku EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Projektów witryny sieci Web  
 Te pliki, Utwórz nową witrynę sieci Web w odpowiedzi na **witryny sieci Web platformy ASP.NET** polecenia, które jest dostępne po wskazaniu **nową witrynę sieci Web** na **pliku** menu:  
  
- Default.aspx  
  
     Domyślną stronę główną dla nowej witryny sieci Web. Atrybut Language określa język plik codebehind i atrybut CodeFile określa pliku zależnego zawierające kod codebehind skojarzony z tą stroną.  
  
- Default.aspx.*extension*  
  
     Plik zależny zawiera kod codebehind domyślną stronę główną. Określa język codebehind *rozszerzenia* tego pliku.  
  
- web.config  
  
     Główny plik konfiguracji web.site.  
  
- WebApplication.vstemplate  
  
     Plik szablonu, który określa zawartości rozwiązania witryny sieci Web i wymuszenie utworzenia w folderze App_Data.  
  
- WebApplication.webproj  
  
     Ten plik jest pozostałością system szablonu projektu. Spełnia odwołanie do pliku projektu w pliku WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Projekty usługi w sieci Web  
 Te pliki, Utwórz nową witrynę sieci Web w odpowiedzi na **usługi sieci Web ASP.NET** polecenia, który jest dostępny po wskazaniu **nową witrynę sieci Web** na **pliku** menu:  
  
- Service.asmx  
  
     Strona HTML dla nowej usługi sieci Web. Atrybut Language określa język codebehind, a atrybut CodeBehind określa pliku zależnego zawierające kod codebehind skojarzonego z tą usługą.  
  
- Usługa. *Rozszerzenie*  
  
     Plik zależny, który implementuje klasa usługi. Określa język codebehind *rozszerzenia* tego pliku.  
  
- web.config  
  
- Główny plik konfiguracji web.site.  
  
- WebService.vstemplate  
  
     Plik szablonu, który określa zawartości rozwiązania witryny sieci Web i wymuszenie utworzenia App_Data i App_Code folderów. Usługa. *rozszerzenia* plik jest kopiowany do folderu App_Code.  
  
- WebService.webproj  
  
     Ten plik jest pozostałością system szablonu projektu. Spełnia odwołanie do pliku projektu w pliku WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Folder szablonu elementu projektu  
 Szablony szablonu elementu projektu sieci Web są instalowane w [*ścieżkę instalacji w usłudze Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, każdy w podfolderze o nazwie po jego sieci web języka programowania.  
  
## <a name="project-item-templates"></a>Szablony elementów projektu  
 Szablony elementów projektu witryny sieci Web są używane do dodawania nowych stron sieci Web do witryny sieci Web w taki sposób, w odpowiedzi na **Dodaj istniejący element** polecenia. Tego rodzaju strony sieci Web są obecnie obsługiwane:  
  
- Nowa klasa  
  
- Nowa strona HTML  
  
- Nowy formularz sieci Web  
  
- Nową stronę wzorcową  
  
### <a name="new-class"></a>Nowa klasa  
 Ten szablon tworzy nowy plik źródłowy, który definiuje pustą klasę w odpowiedzi na **Dodaj nową klasę** polecenia.  
  
- Klasa. *Rozszerzenie*  
  
     Plik źródłowy, który implementuje pustą klasę. Określa język codebehind *rozszerzenia* tego pliku.  
  
- Class.vstemplate  
  
     Plik szablonu, tworzy plik źródłowy, który określa jego zawartość.  
  
### <a name="new-html-page"></a>Nowa strona HTML  
 Ten szablon umożliwia utworzenie nowej strony sieci Web w odpowiedzi na **Dodaj nową stronę HTML** polecenia.  
  
- HTMLPage.htm  
  
     Począwszy od zawartość strony sieci Web. Ta strona sieci Web zwykle nie ma skojarzonego pliku codebehind zależne pliku. Aby utworzyć stronę inteligentnych przy użyciu pliku codebehind skojarzony, należy użyć szablonu formularza sieci Web.  
  
- HTMLPage.vstemplate  
  
     Plik szablonu, tworzy stronę sieci Web, która określa jego zawartość.  
  
### <a name="new-webform"></a>Nowy formularz sieci Web  
 Ten szablon umożliwia utworzenie nowej strony internetowej inteligentne w odpowiedzi na **Dodaj nowy formularz sieci Web** polecenia.  
  
 Aby utworzyć plik codebehind zależne źródła, wybierz **umieść kod w oddzielnym pliku**. W przeciwnym razie pojedynczej strony sieci Web jest utworzony z blokiem skryptu pusta i nie \<% strony % > dyrektywy można dołączyć pliku zależnego.  
  
 Aby utworzyć stronę zawartości dla wybranej strony wzorcowej, wybierz **wybierz stronę wzorcową**.  
  
- WebForm.aspx  
  
     Począwszy od zawartość strony sieci Web. Ta strona sieci Web nie ma skojarzonego pliku codebehind zależne pliku.  
  
- WebForm_cb.aspx  
  
     Począwszy od zawartość strony sieci Web. Ta strona sieci Web ma skojarzony plik codebehind plik zależne.  
  
- Plik CodeBehind. *Rozszerzenie*  
  
     Plik zależny, który implementuje klasa formularz sieci Web. Określa język codebehind *rozszerzenia* tego pliku.  
  
- ContentPage.aspx  
  
     Począwszy od zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web nie ma skojarzonego pliku codebehind zależne pliku.  
  
- ContentPage_cb.aspx  
  
     Począwszy od zawartość strony sieci Web jako strony zawartości. Ta strona sieci Web ma skojarzony plik codebehind plik zależne.  
  
- WebForm.vstemplate  
  
     Plik szablonu, określająca zawartość nowej strony sieci web i jego plików zależnych, jeśli istnieje.  
  
### <a name="new-master-page"></a>Nowa strona wzorcowa  
 Ten szablon umożliwia utworzenie nowej strony wzorcowej w odpowiedzi na **Dodaj nową stronę wzorcową** polecenia.  
  
 Aby utworzyć plik codebehind zależne źródła, wybierz **umieść kod w oddzielnym pliku**. W przeciwnym razie pojedynczej strony sieci Web jest utworzony z blokiem skryptu pusta i nie \<% strony % > dyrektywy można dołączyć pliku zależnego.  
  
- MasterPage.master  
  
     Począwszy od zawartość strony wzorcowej. Ta strona wzorcowa nie ma skojarzonego pliku codebehind zależne pliku.  
  
- MasterPage_cb.master  
  
     Począwszy od zawartość strony wzorcowej. Ta strona wzorcowa ma skojarzony plik codebehind pliku zależnego.  
  
- Plik CodeBehind. *rozszerzenia*  
  
     Plik zależny, który implementuje klasa strony wzorcowej. Określa język codebehind *rozszerzenia* tego pliku.  
  
- MasterPage.vstemplate  
  
     Plik szablonu, określająca zawartość nowej strony wzorcowej i jego plików zależnych, jeśli istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
