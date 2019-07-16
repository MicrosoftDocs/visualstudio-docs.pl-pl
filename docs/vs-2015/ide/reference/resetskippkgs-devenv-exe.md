---
title: -ResetSkipPkgs (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 44e2cb42bf6bf8c1a61512713e9fc87cbe8f0901
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182376"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Czyści wszystkie opcje, aby pominąć ładowanie dodane do VSPackages przez użytkowników, które chcą uniknąć obciążania problem pakietów VSPackage, a następnie uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Uwagi  
 Obecność tagu SkipLoading powoduje wyłączenie ładowania pakietu VSPackage; czyszczenie tagu włączające ładowania pakietu VSPackage.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład czyści wszystkie tagi SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
