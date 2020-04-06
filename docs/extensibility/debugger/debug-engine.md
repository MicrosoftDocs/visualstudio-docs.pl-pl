---
title: Aparat debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739069"
---
# <a name="debug-engine"></a>Aparat debugowania
Aparat debugowania (DE) współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania, takich jak kontrola wykonania, punkty przerwania i ocena wyrażeń. DE jest odpowiedzialny za monitorowanie stanu programu jest debugowane. Aby to zrobić, DE używa niezależnie od metod są dostępne dla niego w obsługiwanym czasie wykonywania, czy z procesora CPU lub z interfejsów API dostarczonych przez środowisko wykonawcze.

 Na przykład środowisko uruchomieniowe języka wspólnego (CLR) dostarcza mechanizmy do monitorowania uruchomionego programu za pośrednictwem interfejsów ICorDebugXXX. DE, który obsługuje CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia programu kodu zarządzanego jest debugowany. Następnie komunikuje wszelkie zmiany stanu do menedżera debugowania sesji (SDM), który przekazuje takie informacje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, czyli systemu, w którym uruchamia się debugowany program. Środowisko CLR jest środowiskiem uruchomieniowym dla kodu zarządzanego, a środowisko wykonawcze Win32 jest przeznaczone dla natywnych aplikacji systemu Windows. Jeśli język, który tworzysz może kierować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jeden z tych dwóch uruchomień, już dostarcza niezbędne aparaty debugowania. Wszystko, co musisz zaimplementować, to oceniający wyrażenie.

## <a name="debug-engine-operation"></a>Działanie aparatu debugowania
 Usługi monitorowania są implementowane za pośrednictwem interfejsów DE i może spowodować pakiet debugowania do przejścia między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zazwyczaj istnieje tylko jedna implementacja DE na środowisko wykonawcze.

> [!NOTE]
> Chociaż istnieją oddzielne implementacje DE dla [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]Transact-SQL [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] i , VBScript i udostępnić jeden DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie umożliwia aparaty debugowania, aby uruchomić jeden z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dwóch sposobów: w tym samym procesie co powłoki lub w tym samym procesie, co program docelowy jest debugowany. Ten ostatni formularz zwykle występuje, gdy proces debugowany jest faktycznie skrypt uruchomiony pod interpreterem. Aparat debugowania musi mieć intymną wiedzę interpretera w celu monitorowania skryptu. W takim przypadku interpreter jest faktycznie środowisko uruchomieniowe; aparaty debugowania są dla określonych implementacji środowiska uruchomieniowego. Ponadto implementacja pojedynczego DE można podzielić na granice procesu i komputera (na przykład zdalne debugowanie).

 DE udostępnia interfejsy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania. Cała komunikacja odbywa się za pośrednictwem COM. Niezależnie od tego, czy DE jest ładowany w procesie, poza procesem, czy na innym komputerze, nie ma to wpływu na komunikację składników.

 DE współpracuje ze składnikiem oceniającego wyrażenie, aby włączyć DE dla danego środowiska wykonawczego, aby zrozumieć składnię wyrażeń. DE współpracuje również ze składnikiem obsługi symboli, aby uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka. Aby uzyskać więcej informacji, zobacz [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [Dostawca symboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Wyrażenie](../../extensibility/debugger/expression-evaluator.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
