---
title: Tworzenie nadrzędnych folderów kontenera dla rozwiązań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6845e867a8c5fd0ef2b367dc5f2e3b5760869746
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602018"
---
# <a name="create-parent-container-folders-for-solutions"></a>Tworzenie folderów kontenera dla rozwiązań nadrzędnego
W źródło sterowania wtyczki interfejsu API w wersji 1.2 użytkownik może określić lokalizację docelową kontroli źródła z jednym elementem głównym dla wszystkich projektów sieci web w ramach rozwiązania. To z jednym elementem głównym jest nazywany Super Unified głównego (dolna Południowa).

 W źródło sterowania wtyczki interfejsu API w wersji 1.1 Jeśli użytkownik dodany rozwiązania wieloprojektowy służący do kontroli źródła, użytkownik został monit o określenie jednego miejsca przeznaczenia kontroli źródła dla każdego projektu sieci web.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nowe funkcje
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE prawie zawsze tworzy SUR folder podczas dodawania rozwiązanie do kontroli źródła. W szczególności odbywa się to w następujących przypadkach:

-   Projekt jest projektem sieci web udziału plików.

-   Istnieją różne dyski dla projektu i pliku rozwiązania.

-   Istnieją różne udziały plików rozwiązania i projektu.

-   Projekt został dodany osobno (w ramach rozwiązania pod kontrolą źródła).


W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], zalecane jest, czy nazwa folderu SUR być taka sama jak nazwa rozwiązania bez rozszerzenia. W poniższej tabeli podsumowano zachowanie w dwóch wersjach.

|Funkcja|Wtyczka interfejsu API w wersji 1.1 kontroli źródła|Wtyczka API w wersji 1.2 kontroli źródła|
|-------------| - | - |
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Dodaj projekt do rozwiązania pod kontrolą źródła|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Uwaga:**  Program Visual Studio zakłada, że rozwiązanie jest element podrzędny elementu SUR.|

## <a name="examples"></a>Przykłady
 Poniższa lista zawiera dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownik jest monitowany o lokalizację docelową dla rozwiązania pod kontrolą źródła dopóki *user_choice* jest określony jako miejsca docelowego. User_choice jest określony, zostaną dodane rozwiązanie i dwa projekty bez monitowania użytkownika o lokalizacji docelowych kontroli źródła.

|Rozwiązanie zawiera|W lokalizacji dysku|Struktura domyślnej bazy danych|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Między serwerem Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Między serwerem Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 SUR folder i podfoldery są tworzone niezależnie od tego, czy operacja została anulowana lub nie powiedzie się z powodu błędu. Ich nie są automatycznie usuwane w warunkach anulowania lub błędu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Wartość domyślna to zachowanie w wersji 1.1, jeśli wtyczka do kontroli źródła nie może zwracać `SCC_CAP_CREATESUBPROJECT` i `SCC_CAP_GETPARENTPROJECT` flag funkcji. Ponadto użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można przywrócić, ustawiając wartość następujący klucz do zachowania w wersji 1.1 *DWORD: 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Zobacz także
- [What's new in źródła kontrolki wtyczki API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)