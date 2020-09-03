---
title: Tworzenie nadrzędnych folderów kontenerów dla rozwiązań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196930"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Tworzenie nadrzędnych folderów kontenera dla rozwiązań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W interfejsie API wtyczki kontroli źródła w wersji 1,2 użytkownik może określić pojedyncze miejsce docelowe kontroli źródła dla wszystkich projektów sieci Web w ramach rozwiązania. Ten pojedynczy katalog główny nosi nazwę nieujednolicony katalog główny (SUR).  
  
 W interfejsie API wtyczki kontroli źródła w wersji 1,1, jeśli użytkownik dodał rozwiązanie z obsługą wielu projektów do kontroli źródła, użytkownik był monitowany o określenie jednego miejsca docelowego kontroli źródła dla każdego projektu sieci Web.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE niemal zawsze tworzy folder sur podczas dodawania rozwiązania do kontroli źródła. W związku z tym robi to w następujących przypadkach:  
  
- Projekt jest projektem sieci Web udziału plików.  
  
- Istnieją różne dyski dla projektu i pliku rozwiązania.  
  
- Istnieją różne udziały dla projektu i pliku rozwiązania.  
  
- Projekty zostały dodane osobno (w rozwiązaniu kontrolowanym przez źródło).  
  
  Zaleca się [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aby nazwa folderu sur była taka sama jak nazwa rozwiązania bez rozszerzenia. Poniższa tabela zawiera podsumowanie zachowania w obu wersjach.  
  
|Cechy|Interfejs API wtyczki kontroli tSource w wersji 1,1|Interfejs API wtyczki kontroli źródła w wersji 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Dodaj projekt do rozwiązania kontrolowanego przez Źródło|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject () **Uwaga:**  program Visual Studio zakłada, że rozwiązanie jest bezpośrednim elementem podrzędnym sur.|  
  
## <a name="examples"></a>Przykłady  
 W poniższej tabeli przedstawiono dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] użytkownik jest monitowany o lokalizację docelową dla rozwiązania pod kontrolą źródła, dopóki  *user_choice* nie zostanie określona jako miejsce docelowe. Gdy user_choice jest określony, rozwiązanie i dwa projekty są dodawane bez monitowania użytkownika o miejsca docelowe kontroli źródła.  
  
|Rozwiązanie zawiera|Lokalizacje na dysku|Domyślna struktura bazy danych|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Sieci Web 1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/WEB1<br /><br /> $/*user_choice*/web2|  
|sln1. sln<br /><br /> Sieci Web 1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/WEB1<br /><br /> $/*user_choice*/sln1/Win1|  
  
 Folder i podfoldery SUR są tworzone bez względu na to, czy operacja została anulowana, czy niepowodzeniem z powodu błędu. Nie są automatycznie usuwane w warunkach anulowania lub błędu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] domyślnie działa w wersji 1,1, jeśli wtyczka kontroli źródła nie zwraca `SCC_CAP_CREATESUBPROJECT` i `SCC_CAP_GETPARENTPROJECT` flaguje możliwości. Ponadto użytkownicy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mogą zdecydować się na powracanie do zachowania wersji 1,1 przez ustawienie wartości następującego klucza na DWORD: 00000001:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
