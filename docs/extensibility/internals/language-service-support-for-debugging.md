---
title: Obsługa usługi językowej do debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707435"
---
# <a name="language-service-support-for-debugging"></a>Obsługa usługi językowej do debugowania
Usługa języka może zapewnić funkcje, które <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> obsługują debugera za pośrednictwem interfejsu. Funkcje te obejmują sprawdzanie poprawności punktów przerwania i dostarczanie listy wyrażeń do okna **Autos.**

 Jednak musisz mieć oceniającego wyrażenie do debugowania języka. Oceniający wyrażenie jest odpowiedzialny za ocenę wyrażeń do tworzenia wartości podczas debugowania. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz:

- [Oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Przykład oceniającego wyrażenia zarządzanego](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Dane wyjściowe kompilatora
 Typ kompilatora określa, co należy zrobić, aby zaimplementować debugowanie dla języka. Jeśli kompilator jest przeznaczony dla systemu operacyjnego Windows i zapisuje plik pdb, można debugować programy za pomocą aparatu debugowania kodu macierzystego, który jest zintegrowany z programem Visual Studio. Jeśli kompilator tworzy język pośredni firmy Microsoft (MSIL), można debugować programy za pomocą aparatu debugowania kodu zarządzanego, który jest również zintegrowany z programem Visual Studio. Jeśli kompilator jest przeznaczony dla własnego systemu operacyjnego lub innego środowiska wykonawczego, należy napisać własny aparat debugowania.

 Aby uzyskać więcej informacji na temat implementowania debugowania dla języka, zobacz [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) w visual studio debugowania SDK.
