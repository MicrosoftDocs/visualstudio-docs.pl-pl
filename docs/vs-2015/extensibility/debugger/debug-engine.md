---
title: Aparat debugowania | Dokumentacja firmy Microsoft
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
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf2335b907601bb17276b06ae1bef033a1641515
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733330"
---
# <a name="debug-engine"></a>Aparat debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania (DE) współpracuje z interpreter lub systemu operacyjnego w celu dostarczania usług debugowania, takie jak wykonanie kontroli, punkty przerwania i wyrażenie oceny. DE jest odpowiedzialny za monitorowanie stanu debugowanego programu. Aby to osiągnąć, DE używa, niezależnie od metody są dostępne obsługiwane środowisko uruchomieniowe, czy z procesora CPU lub za pomocą interfejsów API dostarczonych przez środowisko uruchomieniowe.  
  
 Na przykład środowisko uruchomieniowe języka wspólnego (CLR) dostarcza mechanizmów monitorowania za pośrednictwem interfejsów ICorDebugXXX uruchomionego programu. DE, który obsługuje środowisko CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia kodu zarządzanego debugowanego. Następnie przesyła zmiany stanu do Menedżer debugowania sesji (SDM), która przekazuje informacje do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, oznacza to, w którym program debugowany uruchomienia systemu. Środowisko CLR jest środowiskiem uruchomieniowym na potrzeby kodu zarządzanego, a środowisko wykonawcze systemu Win32 jest dla natywnych aplikacji Windows. Jeśli język, możesz utworzyć można wskazać jeden z tych dwóch środowisk uruchomieniowych [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dostarcza już aparaty debugowania konieczne. Wszystko, co trzeba implementować to ewaluatora wyrażeń.  
  
## <a name="debug-engine-operation"></a>Operacja aparatu debugowania  
 Usługi monitorowania są implementowane za pośrednictwem interfejsów DE i może spowodować, że debugowanie pakietu, do którego nastąpi przejście między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zazwyczaj jest tylko jedna implementacja DE na środowisku uruchomieniowym.  
  
> [!NOTE]
>  Istnieją osobne implementacje DE języka Transact-SQL i [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], VBScript i [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] udostępniać pojedynczy DE.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie umożliwia debugowanie silników na jeden z dwóch sposobów: w tym samym procesie co [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoki lub w tym samym procesie co program docelowy debugowania. Drugim formularzu występuje przeważnie debugowanego procesu jest faktycznie skrypt uruchomiony w ramach tłumacza, gdy aparat debugowania musi mieć wiedzy na temat obsługi interpreter, aby monitorować skryptu. Należy pamiętać, że w tym przypadku interpreter faktycznie środowisko uruchomieniowe aparaty debugowania są przeznaczone dla implementacji określonego środowiska uruchomieniowego. Ponadto implementacji pojedynczej DE może zostać podzielony granic procesu i maszynowo, (na przykład, zdalne debugowanie).  
  
 Udostępnia DE [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] profilowanie interfejsów. Cała komunikacja jest za pomocą modelu COM. Czy DE jest ładowany, poza procesem lub na innym komputerze, nie ma wpływu na komunikacji.  
  
 DE współpracuje ze składnikiem ewaluatora wyrażeń umożliwiające DE dla tego określonego czasu wykonywania poznać składnię wyrażeń. DE współpracuje również z składnik obsługi symboli, uzyskiwać dostęp do informacji symbolicznego debugowania generowanych przez kompilator języka. Aby uzyskać więcej informacji, zobacz [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [dostawca symboli](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)

