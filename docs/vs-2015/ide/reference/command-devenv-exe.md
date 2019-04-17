---
title: -Command (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81f57fc6a4d21e1310fbb30d2b2dcaa826ad7685
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662442"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wykonuje określone polecenie po uruchomieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argumenty  
 `CommandName`  
 Wymagana. Pełna nazwa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia lub jego alias, ujęte w podwójny cudzysłów. Aby uzyskać więcej informacji o syntaksie aliasów i poleceń, zobacz [polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Uwagi  
 Po zakończeniu uruchamiania, IDE wykonuje polecenie nazwane. Jeśli używasz tego przełącznika, IDE nie wyświetla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] strony początkowej podczas uruchamiania.  
  
 Jeśli dodatek udostępnia polecenia, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie dodatków za pomocą Menedżera dodatków](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i automatycznie uruchamia makro otwierania ulubionych plików.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
