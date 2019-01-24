---
title: — Uaktualnianie (devenv.exe) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 465c90736f5470f48d47336bc916ca3cb2c09b6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779349"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Aktualizuje plik rozwiązania i wszystkie jego pliki projektu lub pliku projektu, określony do bieżącego [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formatów tych plików.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Za pomocą `/upgrade` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Wyniki procesu uaktualniania można zobaczyć w raporcie uaktualnienia dla rozwoju języka rozwiązania lub projektu. Brak błędów i zużyciu informacji jest zwracana. Aby uzyskać więcej informacji na temat uaktualniania projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], zobacz [jak: Rozwiązywanie problemów z uaktualnieniami projektu nie powiedzie, program Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uaktualnia plik rozwiązania o nazwie "MyProject.sln" w Twoim domyślnym folderze dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozwiązania.  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Rozwiązywanie problemów z uaktualnieniami projektu powiodło się programu Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
