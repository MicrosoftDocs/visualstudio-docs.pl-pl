---
title: Aparat debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e7e5afa4e68d37254c3cb07f1bafa2b48ee787a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336545"
---
# <a name="debug-engine"></a>Aparat debugowania
Aparat debugowania (DE) współpracuje z interpreter lub systemu operacyjnego w celu dostarczania usług debugowania, takie jak wykonanie kontroli, punkty przerwania i wyrażenie oceny. DE jest odpowiedzialny za monitorowanie stanu debugowanego programu. Aby to osiągnąć, DE używa, niezależnie od metody są dostępne obsługiwane środowisko uruchomieniowe, czy z procesora CPU lub za pomocą interfejsów API dostarczonych przez środowisko uruchomieniowe.

 Na przykład środowisko uruchomieniowe języka wspólnego (CLR) dostarcza mechanizmów monitorowania za pośrednictwem interfejsów ICorDebugXXX uruchomionego programu. DE, który obsługuje środowisko CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia kodu zarządzanego debugowanego. Następnie przesyła zmiany stanu do Menedżer debugowania sesji (SDM), która przekazuje informacje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, oznacza to, w którym program debugowany uruchomienia systemu. Środowisko CLR jest środowiskiem uruchomieniowym na potrzeby kodu zarządzanego, a środowisko wykonawcze systemu Win32 jest dla natywnych aplikacji Windows. Jeśli język, możesz utworzyć można wskazać jeden z tych dwóch środowisk uruchomieniowych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza już aparaty debugowania konieczne. Wszystko, co trzeba implementować to ewaluatora wyrażeń.

## <a name="debug-engine-operation"></a>Operacja aparatu debugowania
 Usługi monitorowania są implementowane za pośrednictwem interfejsów DE i może spowodować, że debugowanie pakietu, do którego nastąpi przejście między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zazwyczaj jest tylko jedna implementacja DE na środowisku uruchomieniowym.

> [!NOTE]
> Istnieją osobne implementacje DE języka Transact-SQL i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] udostępniać pojedynczy DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie umożliwia debugowanie silników na jeden z dwóch sposobów: w tym samym procesie co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki lub w tym samym procesie co program docelowy debugowania. Drugim formularzu występuje przeważnie, gdy debugowany proces jest faktycznie skrypt uruchomiony w ramach tłumacza. Aparat debugowania musi mieć wiedzy na temat obsługi interpreter, aby monitorować skryptu. W tym przypadku interpreter jest faktycznie środowisko uruchomieniowe aparaty debugowania są przeznaczone dla implementacji określonego środowiska uruchomieniowego. Ponadto implementacji pojedynczej DE może zostać podzielony granic procesu i maszynowo, (na przykład, zdalne debugowanie).

 Udostępnia DE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] profilowanie interfejsów. Cała komunikacja jest za pomocą modelu COM. Czy DE jest ładowany, poza procesem lub na innym komputerze, nie ma wpływu na komunikacji.

 DE współpracuje ze składnika ewaluatora wyrażeń umożliwiające "de" dla tego konkretnego środowiska uruchomieniowego poznać składnię wyrażeń. DE współpracuje również z składnik obsługi symboli, uzyskiwać dostęp do informacji symbolicznego debugowania generowanych przez kompilator języka. Aby uzyskać więcej informacji, zobacz [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [dostawca symboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Zobacz także
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)