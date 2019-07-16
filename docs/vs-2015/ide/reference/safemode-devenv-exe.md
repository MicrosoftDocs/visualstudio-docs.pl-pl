---
title: -Tryb awaryjny (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94e8e87f4440644f76906a70ea09a46282b109c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163367"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym, ładowanie tylko środowisko domyślne i usługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik uniemożliwia załadowanie, kiedy wszystkich innych pakietów VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozpoczyna się, co pozwala na zapewnienie stabilne wykonywania.  
  
## <a name="description"></a>Opis  
 Poniższy przykład rozpoczyna się [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym.  
  
## <a name="code"></a>Kod  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
