---
title: Szablony pomocy technicznej dla witryn internetowych | Microsoft Docs
description: Dowiedz się więcej o szablonach pomocy technicznej dla witryn internetowych. Visual Studio projektu i elementu witryny sieci Web zapewniają dostosowywalne i wielokrotnego użytku szablony elementów i projektów witryn internetowych, które można dostosowywać.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1bd391d13a6d650cb4d23ce78789a66ef50c2e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898900"
---
# <a name="web-site-support-templates"></a>Szablony pomocy technicznej dotyczącej witryn internetowych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Szablony projektów i elementów witryn internetowych zapewniają możliwość wielokrotnego użytku i dostosowywalnych wycinki elementów i projektów witryn internetowych, które przyspieszają proces tworzenia przez usunięcie konieczności tworzenia nowych projektów i elementów witryny sieci Web od podstaw. Aby uzyskać więcej informacji na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temat szablonów, zobacz [Creating Project and Item Templates (Tworzenie szablonów projektów i elementów).](../../ide/creating-project-and-item-templates.md)

## <a name="project-template-folder"></a>Folder szablonu projektu
 Szablony projektów sieci Web są zwykle instalowane w folderze [*Visual Studio Installation Path*]\Common7\IDE\ProjectTemplates\Web , każdy w podfolderze o nazwie na podstawie języka programowania \\ sieci Web.

## <a name="project-file"></a>Plik projektu
 Zintegrowane środowisko projektowe (IDE) wymaga rozszerzenia pliku projektu jako sposobu mapowania szablonu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na właściwy typ projektu. Ponieważ projekty internetowe nie mają pliku projektu, fikcyjne rozszerzenie pliku projektu .webproj jest rejestrowane w celu mapowania szablonu na typ projektu.

 Opcjonalnie można dodać ciąg nazwy języka do szablonu, aby umożliwić systemowi projektu  sieci Web ustawienie domyślnego języka w oknie dialogowym Dodawanie nowego elementu dla elementów opartych na szablonie. Ciąg musi być pierwszym wierszem pliku. Musi ona być dopasowana zarówno do nazwy zarejestrowanej w obszarze AddItemLanguageName w rejestracji aparatu IntelliSense, jak i nazwy zarejestrowanej w obszarze Project Subtype(VsTemplate). Aby uzyskać więcej informacji, zobacz [Atrybuty pomocy technicznej witryny sieci Web.](../../extensibility/internals/web-site-support-attributes.md)

 Jeśli ciąg nie istnieje, system projektu sieci Web próbuje określić język domyślny na podstawie atrybutu Language i rozszerzeń plików stron dodanych do projektu internetowego przez szablon projektu.

## <a name="project-templates"></a>Szablony projektów
 Szablony projektów witryn internetowych są używane do kompilowania nowych witryn internetowych w odpowiedzi na polecenie Nowa witryna sieci **Web** w menu **Plik.** Obecnie obsługiwane są trzy typy projektów witryn sieci Web:

- Puste projekty witryn internetowych

- Projekty witryn internetowych

- Projekty usługi sieci Web

### <a name="empty-web-site-projects"></a>Puste projekty witryn internetowych
 Te pliki tworzą nową pustą witrynę sieci Web w odpowiedzi na polecenie Pusta witryna sieci **Web,** które jest dostępne po wybraniu polecenia **File**  >  New Web Site (Utwórz **nową witrynę sieci Web):**

- EmptyWeb.vstemplate

     Plik szablonu, który kieruje tworzeniem nowej pustej witryny internetowej.

- EmptyWeb.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia odwołanie do pliku projektu w pliku EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Projekty witryn internetowych
 Te pliki tworzą nową witrynę sieci Web w odpowiedzi na polecenie **ASP.NET Web Site,** które jest dostępne po wybraniu polecenia **File** New Web Site (Utwórz nową  >  **witrynę sieci Web):**

- Default.aspx

     Domyślna strona główna nowej witryny internetowej. Atrybut Language określa język codebehind, a atrybut CodeFile określa plik zależny, który zawiera kod bez kodu skojarzony z tą stroną.

- Default.aspx. *rozszerzenie*

     Plik zależny, który zawiera kodbehind domyślnej strony głównej. Język codebehind określa *rozszerzenie* tego pliku.

- web.config

     Plik konfiguracji web.site głównego.

- WebApplication.vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza utworzenie App_Data sieci Web.

- WebApplication.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia on wymagania odwołania do pliku projektu w pliku WebApplication.vstemplate.

### <a name="web-service-projects"></a>Projekty usługi sieci Web
 Te pliki tworzą nową witrynę internetową w odpowiedzi na polecenie **ASP.NET Web Service,** które jest dostępne po wybraniu polecenia **File** New Web  >  Site (Utwórz **nową witrynę sieci Web):**

- Service.asmx

     Strona HTML dla nowej usługi internetowej. Atrybut Language określa język codebehind, a atrybut CodeBehind określa plik zależny, który zawiera kodbehind skojarzony z tą usługą.

- Usługi. *Rozszerzenie*

     Plik zależny, który implementuje klasę usługi. Język codebehind określa *rozszerzenie* tego pliku.

- web.config

- Plik konfiguracji web.site głównego.

- WebService.vstemplate

     Plik szablonu, który określa zawartość rozwiązania witryny sieci Web i wymusza tworzenie folderów App_Data i App_Code sieci Web. Usługa. *Plik* rozszerzenia jest kopiowany do App_Code folderze.

- WebService.webproj

     Ten plik jest artefaktem systemu szablonów projektu. Spełnia on wymagania odwołania do pliku projektu w pliku WebService.vstemplate.

## <a name="project-item-template-folder"></a>Folder szablonu elementu projektu
 Szablony elementów projektu sieci Web są zwykle instalowane w folderze [*Visual Studio Ścieżka* instalacji ]\Common7\IDE\ItemTemplates\Web , każdy w podfolderze o nazwie na podstawie języka programowania sieci \\ Web.

## <a name="project-item-templates"></a>Szablony elementów projektu
 Szablony elementów projektu witryny sieci Web służą do dodawania nowych stron sieci Web do witryny sieci Web w odpowiedzi na polecenie **Dodaj istniejący** element. Tego rodzaju strony sieci Web są obecnie obsługiwane:

- Nowa klasa

- Nowa strona HTML

- Nowy formularz sieci Web

- Nowa strona wzorcowa

### <a name="new-class"></a>Nowa klasa
 Ten szablon tworzy nowy plik źródłowy, który definiuje pustą klasę w odpowiedzi na polecenie **Dodaj nową klasę.**

- Klasa. *Rozszerzenie*

     Plik źródłowy, który implementuje pustą klasę. Język codebehind określa *rozszerzenie* tego pliku.

- Class.vstemplate

     Plik szablonu, który tworzy plik źródłowy i określa jego zawartość.

### <a name="new-html-page"></a>Nowa strona HTML
 Ten szablon tworzy nową stronę internetową w odpowiedzi na polecenie **Dodaj nową stronę HTML.**

- HTMLPage.htm

     Początkowa zawartość strony internetowej. Ta strona internetowa zazwyczaj nie ma skojarzonego pliku zależnego bez kodu. Aby utworzyć stronę inteligentną ze skojarzonym plikiem codebehind, użyj szablonu formularza sieci Web.

- HTMLPage.vstemplate

     Plik szablonu, który tworzy stronę internetową i określa jej zawartość.

### <a name="new-webform"></a>Nowy formularz WebForm
 Ten szablon tworzy nową inteligentną stronę internetową w odpowiedzi na polecenie **Dodaj nowy formularz** sieci Web.

 Aby utworzyć zależny plik źródłowy kodubehind, wybierz **pozycję Umieść kod w oddzielnym pliku**. W przeciwnym razie tworzona jest pojedyncza strona internetowa, która ma pusty blok skryptów i nie ma dyrektyw do \<% Page %> podłączania pliku zależnego.

 Aby utworzyć stronę zawartości dla wybranej strony wzorcowej, wybierz **pozycję Wybierz stronę wzorcową.**

- WebForm.aspx

     Początkowa zawartość strony internetowej. Ta strona internetowa nie ma skojarzonego pliku zależnego bez kodu.

- WebForm_cb.aspx

     Początkowa zawartość strony internetowej. Ta strona internetowa ma skojarzony plik zależny od kodu.

- Bez codebehind. *Rozszerzenie*

     Plik zależny, który implementuje klasę formularzy internetowych. Język codebehind określa *rozszerzenie* tego pliku.

- ContentPage.aspx

     Początkowa zawartość strony internetowej jako strona zawartości. Ta strona internetowa nie ma skojarzonego pliku zależnego bez kodu.

- ContentPage_cb.aspx

     Początkowa zawartość strony internetowej jako strona zawartości. Ta strona internetowa ma skojarzony plik zależny od kodu.

- WebForm.vstemplate

     Plik szablonu, który określa zawartość nowej strony internetowej i jej pliku zależnego, jeśli taki jest.

### <a name="new-master-page"></a>Nowa strona wzorcowa
 Ten szablon tworzy nową stronę wzorcową w odpowiedzi na polecenie **Dodaj nową stronę wzorcową.**

 Aby utworzyć zależny plik źródłowy kodubehind, wybierz **pozycję Umieść kod w oddzielnym pliku**. W przeciwnym razie tworzona jest pojedyncza strona internetowa, która ma pusty blok skryptów i nie ma dyrektyw do \<% Page %> podłączania pliku zależnego.

- MasterPage.master

     Zawartość początkowa strony wzorcowej. Ta strona wzorcowa nie ma skojarzonego pliku zależnego bez kodu.

- MasterPage_cb.master

     Zawartość początkowa strony wzorcowej. Ta strona wzorcowa ma skojarzony plik zależny od kodu.

- Bez codebehind. *rozszerzenie*

     Plik zależny, który implementuje klasę strony wzorcowej. Język codebehind określa *rozszerzenie* tego pliku.

- MasterPage.vstemplate

     Plik szablonu, który określa zawartość nowej strony wzorcowej i jej pliku zależnego, jeśli taki jest.

## <a name="see-also"></a>Zobacz też
- [Pomoc techniczna dotycząca witryny internetowej](../../extensibility/internals/web-site-support.md)
