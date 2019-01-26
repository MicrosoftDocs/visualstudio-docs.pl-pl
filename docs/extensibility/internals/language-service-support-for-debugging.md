---
title: Obsługa usługi językowej do debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ebb0293e17fe022fc04c9e4e6724fa49a8c3056
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994228"
---
# <a name="language-service-support-for-debugging"></a>Obsługa usługi językowej do debugowania
Usługa języka zapewniają funkcje, które obsługują debuger za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfejsu. Funkcje te obejmują sprawdzanie poprawności punktów przerwania i udostępnienie listy wyrażeń **Autos** okna.  
  
 Jednak musisz mieć ewaluatora wyrażeń do debugowania języka. Ewaluator wyrażeń jest odpowiedzialny za wyrażeń do produkcji wartości podczas debugowania. Dla informacji o implementowaniu ewaluatory wyrażeń CLR zobacz:  
  
-   [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Przykładowe ewaluatora wyrażeń zarządzanych](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
 Typ kompilator Określa, co jest potrzebne do zaimplementowania debugowania dla języka. Jeśli kompilator jest przeznaczony dla systemu operacyjnego Windows i zapisuje plik .pdb można debugować programy z kodem natywnym debugowania aparat, który jest zintegrowany z Visual Studio. Jeśli kompilator generuje języka Microsoft intermediate language (MSIL), można debugować programy z kodem zarządzanym, aparat, który jest również zintegrowana w programie Visual Studio do debugowania. Jeśli kompilator jest przeznaczony dla własności systemu operacyjnego lub innego środowiska, należy napisać własnego aparatu debugowania.  
  
 Aby uzyskać więcej informacji na temat implementowania debugowania dla języka, zobacz [wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) w Visual Studio SDK debugowania.