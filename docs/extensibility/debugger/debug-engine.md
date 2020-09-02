---
title: Aparat debugowania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739069"
---
# <a name="debug-engine"></a>Aparat debugowania
Aparat debugowania (DE) współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania, takich jak kontrola wykonywania, punkty przerwania i Obliczanie wyrażenia. DE jest odpowiedzialny za monitorowanie stanu debugowanego programu. Aby to zrobić, w środowisku uruchomieniowym są dostępne wszystkie metody, niezależnie od tego, czy procesor CPU, czy z interfejsów API dostarczonych przez środowisko uruchomieniowe.

 Na przykład mechanizmy środowiska uruchomieniowego języka wspólnego (CLR) do monitorowania działającego programu za pomocą interfejsów ICorDebugXXX. A DE, która obsługuje środowisko CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia debugowanego programu kodu zarządzanego. Następnie komunikuje wszelkie zmiany stanu z menedżerem debugowania sesji (SDM), który przekazuje takie informacje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, czyli systemu, w którym jest uruchamiany debugowany program. CLR to środowisko uruchomieniowe dla kodu zarządzanego, a środowisko uruchomieniowe Win32 jest przeznaczone dla natywnych aplikacji systemu Windows. Jeśli tworzony język może być przeznaczony dla jednego z tych dwóch środowisk uruchomieniowych, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia już niezbędne aparaty debugowania. Wszystko, co musisz zaimplementować, to ewaluatora wyrażeń.

## <a name="debug-engine-operation"></a>Operacja debugowania aparatu
 Usługi monitorowania są implementowane przez wszystkie interfejsy i mogą spowodować przejście pakietu debugowania między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zazwyczaj istnieje tylko jedna cofnięta implementacja dla środowiska wykonawczego.

> [!NOTE]
> Chociaż istnieją oddzielne niewdrożenia dla języka Transact-SQL i języka [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] VBScript i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] udostępniania jednego.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugowanie włącza aparaty debugowania do uruchamiania jeden z dwóch sposobów: w tym samym procesie co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoka lub w tym samym procesie co debugowany program docelowy. Ten ostatni formularz zwykle występuje, gdy debugowany proces jest w rzeczywistości skryptem uruchomionym w ramach interpretera. Aparat debugowania musi mieć intimateą wiedzę dotyczącą interpretera, aby monitorować skrypt. W takim przypadku interpreter jest w rzeczywistości środowiskiem uruchomieniowym; Aparaty debugowania są przeznaczone dla określonych implementacji środowiska uruchomieniowego. Ponadto implementacja pojedynczego elementu DE może być podzielna między procesami i granicami maszyn (na przykład debugowaniem zdalnym).

 Ujawnia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsy debugowania. Cała komunikacja odbywa się za poorednictwem modelu COM. Bez względu na to, czy element DE jest ładowany w procesie, poza procesem, czy też na innym komputerze, nie ma wpływu na komunikację składnika.

 Komunikat DE Works ze składnikiem ewaluatora wyrażeń, aby umożliwić działanie DE dla danego środowiska uruchomieniowego w celu zrozumienia składni wyrażeń. Ponadto współpracuje z składnikiem obsługi symboli, aby uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka. Aby uzyskać więcej informacji, zobacz [ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [dostawca symboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
