---
title: Debugowanie aplikacji w trybie mieszanym | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9c8e9f36e7118b1681701f6c8ac60a5bc851308f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691355"
---
# <a name="debugging-mixed-mode-applications"></a>Debugowanie aplikacji w trybie mieszanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacją trybu mieszanego jest każda aplikacja, która łączy w sobie kod natywny (C++) z kodem zarządzanym (takim jak Visual Basic, Visual C# lub C++ działający w środowisku uruchomieniowym języka wspólnego). Debugowanie aplikacji w trybie mieszanym jest w dużej mierze przejrzyste w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; nie jest zbytnio od debugowania aplikacji w trybie pojedynczym. Istnieje jednak kilka specjalnych okoliczności.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Włącz edycję i kontynuację w języku C++ w debugowaniu trybu mieszanego  
  
- Aby użyć funkcji edycji i kontynuacji dla C++ w Visual Studio 2013, musisz powrócić do starego aparatu debugowania. Zobacz [przełączanie do zarządzanego trybu zgodności programu Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) na blogu zarządzania cyklem życia aplikacji firmy Microsoft.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Ocena właściwości aplikacji w trybie mieszanym  
 W aplikacji trybu mieszanego ocena właściwości przez debuger jest kosztowną operacją. W rezultacie operacje debugowania, takie jak przechodzenie mogą, być wykonywane powoli. Aby uzyskać więcej informacji, zobacz [przechodzenie krok po kroku](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9). W przypadku wystąpienia niskiej wydajności w debugowaniu trybu mieszanego, można wyłączyć oceny właściwości w oknie debugera.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Aby wyłączyć funkcję oceny właściwości  
  
1. Na **narzędzia** menu, wybierz **opcje**.  
  
2. W **opcje** po otwarciu okna dialogowego **debugowanie** i wybierz polecenie **ogólne** kategorii.  
  
3. Wyczyść **Włącz obliczanie właściwości i inne niejawne wywołania funkcji** pole wyboru.  
  
   Ponieważ stosy wywołania natywnego i zarządzanego się różnią, debuger nie zawsze może dostarczyć pełny stos wywołań dla kodu mieszanego. Gdy kod natywny wywołuje kod zarządzany, można zauważyć pewne rozbieżności. Aby uzyskać więcej informacji, zobacz [kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
