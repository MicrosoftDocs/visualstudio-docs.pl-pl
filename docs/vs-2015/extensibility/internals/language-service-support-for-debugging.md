---
title: Obsługa usługi językowej na potrzeby debugowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195001"
---
# <a name="language-service-support-for-debugging"></a>Obsługa usługi językowej do debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługa języka może udostępniać funkcje, które obsługują debuger za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfejsu. Funkcje te obejmują sprawdzanie poprawności punktów przerwania i dostarczanie listy wyrażeń do okna **Autokorekty** .  
  
 Jednak musisz mieć ewaluatora wyrażeń, aby debugować swój język. Ewaluatora wyrażeń jest odpowiedzialny za ocenianie wyrażeń do tworzenia wartości podczas debugowania. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz:  
  
- [Oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Przykład ewaluatora wyrażeń zarządzanych](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
 Typ kompilatora określa, co należy zrobić, aby zaimplementować debugowanie dla danego języka. Jeśli kompilator jest przeznaczony dla systemu operacyjnego Windows i zapisuje plik. pdb, można debugować programy z aparatem debugowania kodu natywnego, który jest zintegrowany z programem Visual Studio. Jeśli kompilator produkuje język pośredni (MSIL) firmy Microsoft, można debugować programy z aparatem debugowania kodu zarządzanego, który również jest zintegrowany z programem Visual Studio. Jeśli kompilator ma zastrzeżony system operacyjny lub inne środowisko uruchomieniowe, należy napisać własny aparat debugowania.  
  
 Aby uzyskać więcej informacji na temat implementowania debugowania dla danego języka, zobacz [wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) w zestawie SDK debugowania programu Visual Studio.
