---
title: Obsługa usługi językowej na potrzeby debugowania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707435"
---
# <a name="language-service-support-for-debugging"></a>Obsługa usługi językowej do debugowania
Usługa języka może udostępniać funkcje, które obsługują debuger za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfejsu. Funkcje te obejmują sprawdzanie poprawności punktów przerwania i dostarczanie listy wyrażeń do okna **Autokorekty** .

 Jednak musisz mieć ewaluatora wyrażeń, aby debugować swój język. Ewaluatora wyrażeń jest odpowiedzialny za ocenianie wyrażeń do tworzenia wartości podczas debugowania. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz:

- [Oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Przykład ewaluatora wyrażeń zarządzanych](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Dane wyjściowe kompilatora
 Typ kompilatora określa, co należy zrobić, aby zaimplementować debugowanie dla danego języka. Jeśli kompilator jest przeznaczony dla systemu operacyjnego Windows i zapisuje plik. pdb, można debugować programy z aparatem debugowania kodu natywnego, który jest zintegrowany z programem Visual Studio. Jeśli kompilator produkuje język pośredni (MSIL) firmy Microsoft, można debugować programy z aparatem debugowania kodu zarządzanego, który również jest zintegrowany z programem Visual Studio. Jeśli kompilator ma zastrzeżony system operacyjny lub inne środowisko uruchomieniowe, należy napisać własny aparat debugowania.

 Aby uzyskać więcej informacji na temat implementowania debugowania dla danego języka, zobacz [wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) w zestawie SDK debugowania programu Visual Studio.
