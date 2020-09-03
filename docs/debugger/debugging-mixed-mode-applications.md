---
title: Debugowanie aplikacji w trybie mieszanym | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ba41447af829a378f70d2286ed7a7b9295ed109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916288"
---
# <a name="debugging-mixed-mode-applications"></a>Debugowanie aplikacji w trybie mieszanym
Aplikacją trybu mieszanego jest każda aplikacja, która łączy w sobie kod natywny (C++) z kodem zarządzanym (takim jak Visual Basic, Visual C# lub C++ działający w środowisku uruchomieniowym języka wspólnego). Debugowanie aplikacji w trybie mieszanym jest w dużym stopniu przezroczyste [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . nie jest zbyt inne niż debugowanie aplikacji jednowęzłowej. Istnieje jednak kilka specjalnych okoliczności.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Włącz edycję i kontynuację w języku C++ w debugowaniu trybu mieszanego

Aby włączyć funkcję Edytuj i Kontynuuj dla języka C++, zobacz [jak włączyć i wyłączyć opcję Edytuj i Kontynuuj](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Aby użyć funkcji edycji i kontynuacji dla C++ w Visual Studio 2013, musisz powrócić do starego aparatu debugowania. Zobacz [przełączanie do trybu zgodności zarządzanej w Visual Studio 2013](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) na blogu zarządzania cyklem życia aplikacji firmy Microsoft.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Ocena właściwości aplikacji w trybie mieszanym
 W aplikacji trybu mieszanego ocena właściwości przez debuger jest kosztowną operacją. W rezultacie operacje debugowania, takie jak przechodzenie mogą, być wykonywane powoli. Aby uzyskać więcej informacji, zobacz [krok po kroku](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). W przypadku wystąpienia niskiej wydajności w debugowaniu trybu mieszanego, można wyłączyć oceny właściwości w oknie debugera.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Aby wyłączyć funkcję oceny właściwości

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. W oknie dialogowym **Opcje** Otwórz folder **debugowanie** i wybierz kategorię **Ogólne** .

3. Wyczyść pole wyboru **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji** .

   Ponieważ stosy wywołania natywnego i zarządzanego się różnią, debuger nie zawsze może dostarczyć pełny stos wywołań dla kodu mieszanego. Gdy kod natywny wywołuje kod zarządzany, można zauważyć pewne rozbieżności. Aby uzyskać więcej informacji, zobacz [mieszany kod i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Zobacz też

- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)