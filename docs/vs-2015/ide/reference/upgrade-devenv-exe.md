---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657897"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aktualizuje plik rozwiązania oraz wszystkie jego pliki projektu lub określony plik projektu do bieżących [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formatów tych plików.

## <a name="syntax"></a>Składnia

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Argumenty
 `SolutionFile` Wymagane, Jeśli uaktualniasz całe rozwiązanie i jego projekty. Ścieżka i nazwa pliku rozwiązania. Można wprowadzić tylko nazwę pliku rozwiązania lub pełną ścieżkę i nazwę pliku rozwiązania. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

 `ProjectFile` Wymagane w przypadku uaktualniania pojedynczego projektu. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić tylko nazwę pliku projektu lub pełną ścieżkę i nazwę pliku projektu. Jeśli folder lub plik o nazwie jeszcze nie istnieje, zostanie utworzony.

## <a name="remarks"></a>Uwagi
 Kopie zapasowe są automatycznie tworzone i kopiowane do katalogu o nazwie kopia zapasowa, który został utworzony w bieżącym katalogu.

 Rozwiązania i projekty z kontrolą źródła muszą zostać wyewidencjonowane przed uaktualnieniem.

 Korzystanie z `/upgrade` przełącznika nie jest uruchamiane [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Wyniki uaktualnienia można zobaczyć w raporcie uaktualnienia dla języka deweloperskiego rozwiązania lub projektu. Nie zwrócono informacji o błędzie ani użyciu. Aby uzyskać więcej informacji na temat uaktualniania projektów w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , zobacz [How to: Rozwiązywanie problemów zakończonych niepowodzeniem uaktualnienia projektu programu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Przykład
 Ten przykład uaktualnia plik rozwiązania o nazwie "Moje Project. sln" w folderze domyślnym dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozwiązań.

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Rozwiązywanie problemów zakończonych niepowodzeniem — uaktualnienia projektu programu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md)
