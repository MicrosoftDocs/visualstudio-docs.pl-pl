---
title: Tworzenie nadrzędnych folderów kontenerów dla rozwiązań | Microsoft Docs
description: Dowiedz się, jak używać interfejsu API wtyczki kontroli źródła w wersji 1,2, aby określić jedną lokalizację docelową kontroli źródła dla wszystkich projektów sieci Web w ramach rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e65da2b50984b0259079a1693dd31d400e1e12e3
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329942"
---
# <a name="create-parent-container-folders-for-solutions"></a>Tworzenie folderów nadrzędnych kontenera dla rozwiązań
W interfejsie API wtyczki kontroli źródła w wersji 1,2 użytkownik może określić pojedyncze miejsce docelowe kontroli źródła dla wszystkich projektów sieci Web w ramach rozwiązania. Ten pojedynczy katalog główny nosi nazwę nieujednolicony katalog główny (SUR).

 W interfejsie API wtyczki kontroli źródła w wersji 1,1, jeśli użytkownik dodał rozwiązanie z obsługą wielu projektów do kontroli źródła, użytkownik był monitowany o określenie jednego miejsca docelowego kontroli źródła dla każdego projektu sieci Web.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nowe funkcje
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE niemal zawsze tworzy folder sur podczas dodawania rozwiązania do kontroli źródła. W związku z tym robi to w następujących przypadkach:

- Projekt jest projektem sieci Web udziału plików.

- Istnieją różne dyski dla projektu i pliku rozwiązania.

- Istnieją różne udziały dla projektu i pliku rozwiązania.

- Projekty zostały dodane osobno (w rozwiązaniu kontrolowanym przez źródło).

W programie zaleca się, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aby nazwa folderu sur była taka sama jak nazwa rozwiązania bez rozszerzenia. Poniższa tabela zawiera podsumowanie zachowania w obu wersjach.

|Cechy|Interfejs API wtyczki kontroli źródła w wersji 1,1|Interfejs API wtyczki kontroli źródła w wersji 1,2|
|-------------| - | - |
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Dodaj projekt do rozwiązania kontrolowanego przez Źródło|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Uwaga:**  Program Visual Studio zakłada, że rozwiązanie jest bezpośrednim elementem podrzędnym SUR.|

## <a name="examples"></a>Przykłady
 W poniższej tabeli przedstawiono dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownik jest monitowany o lokalizację docelową dla rozwiązania pod kontrolą źródła, dopóki  *user_choice* nie zostanie określona jako miejsce docelowe. Gdy user_choice jest określony, rozwiązanie i dwa projekty są dodawane bez monitowania użytkownika o miejsca docelowe kontroli źródła.

|Rozwiązanie zawiera|Lokalizacje na dysku|Domyślna struktura bazy danych|
|-----------------------|-----------------------|--------------------------------|
|*sln1. sln*<br /><br /> Sieci Web 1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/web2|
|*sln1. sln*<br /><br /> Sieci Web 1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/WEB1<br /><br /> $/<user_choice>/sln1/Win1|

 Folder i podfoldery SUR są tworzone bez względu na to, czy operacja została anulowana, czy niepowodzeniem z powodu błędu. Nie są automatycznie usuwane w warunkach anulowania lub błędu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] domyślnie działa w wersji 1,1, jeśli wtyczka kontroli źródła nie zwraca `SCC_CAP_CREATESUBPROJECT` i `SCC_CAP_GETPARENTPROJECT` flaguje możliwości. Ponadto użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą zdecydować się na powracanie do zachowania wersji 1,1 przez ustawienie wartości następującego klucza na *DWORD: 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl**  =  *DWORD: 00000001*

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
