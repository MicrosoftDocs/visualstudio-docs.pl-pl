---
title: Tworzenie nadrzędnych folderów kontenera dla rozwiązań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a65595b7dabc28a6851820141a71460d84a4b73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762527"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Tworzenie nadrzędnych folderów kontenera dla rozwiązań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Źródło sterowania wtyczki interfejsu API w wersji 1.2 użytkownik może określić lokalizację docelową kontroli źródła z jednym elementem głównym dla wszystkich projektów sieci Web w ramach rozwiązania. To z jednym elementem głównym jest nazywany Super Unified głównego (dolna Południowa).  
  
 Źródło sterowania wtyczki interfejsu API w wersji 1.1 Jeśli użytkownik dodany rozwiązania wieloprojektowy służący do kontroli źródła, użytkownik został monit o określenie jedno miejsce docelowe kontroli źródła dla każdego projektu sieci Web.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE prawie zawsze tworzy SUR folder podczas dodawania rozwiązanie do kontroli źródła. W szczególności odbywa się to w następujących przypadkach:  
  
- Projekt jest udział plików projektu sieci Web.  
  
- Istnieją różne dyski dla projektu i pliku rozwiązania.  
  
- Istnieją różne udziały plików rozwiązania i projektu.  
  
- Projekt został dodany osobno (w ramach rozwiązania pod kontrolą źródła).  
  
  W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zalecane jest, czy nazwa folderu SUR być taka sama jak nazwa rozwiązania bez rozszerzenia. W poniższej tabeli podsumowano zachowanie w dwóch wersjach.  
  
|Funkcja|tSource interfejsu API wtyczki kontroli w wersji 1.1|Wtyczka API w wersji 1.2 kontroli źródła|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Dodaj projekt do rozwiązania pod kontrolą źródła|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Uwaga:** programu Visual Studio zakłada, że rozwiązanie jest element podrzędny elementu SUR.|  
  
## <a name="examples"></a>Przykłady  
 Poniższa lista zawiera dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] użytkownik jest monitowany o lokalizację docelową dla rozwiązania pod kontrolą źródła dopóki *user_choice* jest określony jako miejsca docelowego. User_choice jest określony, zostaną dodane rozwiązanie i dwa projekty bez monitowania użytkownika o lokalizacji docelowych kontroli źródła.  
  
|Rozwiązanie zawiera|W lokalizacji dysku|Struktura domyślnej bazy danych|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Między serwerem Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/sieci Web 1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Między serwerem Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/sieci Web 1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 SUR folder i podfoldery są tworzone niezależnie od tego, czy operacja została anulowana lub kończy się niepowodzeniem z powodu błędu. Ich nie są automatycznie usuwane w warunkach anulowania lub błędu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Wartość domyślna to zachowanie w wersji 1.1, jeśli wtyczka do kontroli źródła nie może zwracać `SCC_CAP_CREATESUBPROJECT` i `SCC_CAP_GETPARENTPROJECT` flag funkcji. Ponadto użytkownicy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] można wybrać powrócić do zachowania w wersji 1.1, ustawiając wartość następującego klucza DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

