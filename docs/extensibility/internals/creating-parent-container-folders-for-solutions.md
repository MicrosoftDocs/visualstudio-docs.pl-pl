---
title: Tworzenie nadrzędnych folderów kontenerów dla rozwiązań | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709102"
---
# <a name="create-parent-container-folders-for-solutions"></a>Tworzenie nadrzędnych folderów kontenerów dla rozwiązań
W interfejsie API wtyczki kontroli źródła w wersji 1.2 użytkownik może określić miejsce docelowe kontroli jednego źródła głównego dla wszystkich projektów sieci web w ramach rozwiązania. Ten pojedynczy katalog główny jest nazywany Super Unified Root (SUR).

 W interfejsie API wtyczki kontroli źródła w wersji 1.1, jeśli użytkownik dodał rozwiązanie wieloprojektowe do kontroli źródła, użytkownik został poproszony o określenie jednego miejsca docelowego kontroli źródła dla każdego projektu sieci web.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nowe funkcje
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prawie zawsze tworzy folder SUR podczas dodawania rozwiązania do kontroli źródła. W szczególności czyni to w następujących przypadkach:

- Projekt jest projektem internetowym udostępniania plików.

- Istnieją różne dyski dla projektu i pliku rozwiązania.

- Istnieją różne udziały dla projektu i pliku rozwiązania.

- Projekty zostały dodane oddzielnie (w rozwiązaniu kontrolowanym przez źródło).

W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], sugeruje się, że nazwa folderu SUR być taka sama jak nazwa rozwiązania bez rozszerzenia. W poniższej tabeli podsumowano zachowanie w dwóch wersjach.

|Funkcja|Interfejs API wtyczki kontroli źródła w wersji 1.1|Interfejs API wtyczki kontroli źródła w wersji 1.2|
|-------------| - | - |
|Dodaj rozwiązanie do SCC|SccInitialize()<br /><br /> Ścieżka SccGetProjPath()<br /><br /> Ścieżka SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> Ścieżka SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Dodawanie projektu do rozwiązania sterowanego źródłem|Ścieżka SccGetProjPath()<br /><br /> OpenProject()|Ścieżka SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Uwaga:**  Visual Studio zakłada, że rozwiązanie jest bezpośrednim podrzędnym sur.|

## <a name="examples"></a>Przykłady
 W poniższej tabeli wymieniono dwa przykłady. W obu przypadkach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownik jest monitowany o lokalizację docelową dla rozwiązania pod kontrolą źródła, dopóki *user_choice* nie zostanie określony jako miejsce docelowe. Po określeniu user_choice rozwiązanie i dwa projekty są dodawane bez monitowania użytkownika o miejsca docelowe kontroli źródła.

|Rozwiązanie zawiera|W lokalizacjach dysków|Domyślna struktura bazy danych|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Sieć Web1<br /><br /> Sieć Web2|*C:\Rozwiązania\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Sieć Web1<br /><br /> Win1 (win1)|*C:\Rozwiązania\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>>/sln1/win1|

 Folder SUR i podfoldery są tworzone niezależnie od tego, czy operacja została anulowana, czy nie powiedzie się z powodu błędu. Nie są one automatycznie usuwane w warunkach anuluj lub błędu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]domyślnie zachowanie w wersji 1.1, jeśli wtyczka `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` kontroli źródła nie zwraca i flagi możliwości. Ponadto użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą powrócić do zachowania w wersji 1.1, ustawiając wartość następującego *klucza na dword:00000001:*

 **[HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\8.0\Kontrola źródła] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API wtyczki kontroli źródła w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
