---
title: -Upgrade (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46e549dfdc661819dac00d0aa965616462130ad0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944726"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aktualizuje plik rozwiązania i wszystkie jego pliki projektu lub pliku projektu, określony do bieżącego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formatów tych plików.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Argumenty
 `SolutionFile`

 Wymagane, jeśli aktualizujesz całe rozwiązanie i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania, lub pełną ścieżkę i nazwę pliku rozwiązania. Folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

 `ProjectFile`

 Wymagane, jeśli w trakcie uaktualniania jednego projektu. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić tylko nazwę pliku projektu, lub pełną ścieżkę i nazwę pliku projektu. Folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

## <a name="remarks"></a>Uwagi
 Kopie zapasowe są automatycznie tworzone i kopiowane do katalogu o nazwie kopia zapasowa, który jest tworzony w bieżącym katalogu.

 Rozwiązania kontrolowanego źródła lub projekty musza być sprawdzone zanim będą mogły być uaktualnione.

 Za pomocą `/upgrade` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Wyniki procesu uaktualniania można zobaczyć w raporcie uaktualnienia dla rozwoju języka rozwiązania lub projektu. Brak błędów i zużyciu informacji jest zwracana. Aby uzyskać więcej informacji na temat uaktualniania projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Przykład
 W tym przykładzie uaktualnia plik rozwiązania o nazwie "MyProject.sln" w Twoim domyślnym folderze dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozwiązania.

```cmd
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)