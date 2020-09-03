---
title: Debugowanie aplikacji w trybie mieszanym | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b462d5d0c449b8e47c936242908e5bbe6e433429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298312"
---
# <a name="debugging-mixed-mode-applications"></a>Debugowanie aplikacji w trybie mieszanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacją trybu mieszanego jest każda aplikacja, która łączy w sobie kod natywny (C++) z kodem zarządzanym (takim jak Visual Basic, Visual C# lub C++ działający w środowisku uruchomieniowym języka wspólnego). Debugowanie aplikacji w trybie mieszanym jest w dużym stopniu przezroczyste [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . nie jest zbyt inne niż debugowanie aplikacji jednowęzłowej. Istnieje jednak kilka specjalnych okoliczności.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Włącz edycję i kontynuację w języku C++ w debugowaniu trybu mieszanego  
  
- Aby użyć funkcji edycji i kontynuacji dla C++ w Visual Studio 2013, musisz powrócić do starego aparatu debugowania. Zobacz [przełączanie do trybu zgodności zarządzanej w Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) na blogu zarządzania cyklem życia aplikacji firmy Microsoft.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Ocena właściwości aplikacji w trybie mieszanym  
 W aplikacji trybu mieszanego ocena właściwości przez debuger jest kosztowną operacją. W rezultacie operacje debugowania, takie jak przechodzenie mogą, być wykonywane powoli. Aby uzyskać więcej informacji, zobacz [krok po kroku](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9). W przypadku wystąpienia niskiej wydajności w debugowaniu trybu mieszanego, można wyłączyć oceny właściwości w oknie debugera.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Aby wyłączyć funkcję oceny właściwości  
  
1. W menu **Narzędzia** wybierz polecenie **Opcje**.  
  
2. W oknie dialogowym **Opcje** Otwórz folder **debugowanie** i wybierz kategorię **Ogólne** .  
  
3. Wyczyść pole wyboru **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji** .  
  
   Ponieważ stosy wywołania natywnego i zarządzanego się różnią, debuger nie zawsze może dostarczyć pełny stos wywołań dla kodu mieszanego. Gdy kod natywny wywołuje kod zarządzany, można zauważyć pewne rozbieżności. Aby uzyskać więcej informacji, zobacz [mieszany kod i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
