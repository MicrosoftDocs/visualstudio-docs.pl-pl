---
title: -Setup (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e5bbbf3a1a9601a46aa9d3080f0d20583b43d22
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670241"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wymusza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do scalenia metadanych zasobów, które opisują, menu, paski narzędzi i grup poleceń, ze wszystkich dostępnych pakietów VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni krok w procesie instalacji programu. Korzystanie z `/setup` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Należy uruchomić `devenv` jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono ostatni krok w instalacji wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawierającej pakietów VSPackage.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
