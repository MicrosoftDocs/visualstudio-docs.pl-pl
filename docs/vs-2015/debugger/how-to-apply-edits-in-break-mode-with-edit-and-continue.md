---
title: 'Instrukcje: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795657"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Porady: stosowanie edycji w trybie przerwania za pomocą pleceń Edytuj i Kontynuuj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć Edytuj i Kontynuuj, aby edytować swój kod w trybie przerwania, a następnie kontynuować bez zatrzymywania i ponownego uruchamiania.  
  
 Edytuj i Kontynuuj nie są dostępne w następujących scenariuszach debugowania:  
  
- Debugowanie w trybie mieszanym (natywnym/zarządzanym).  
  
- Debugowanie SQL.  
  
- Debugowanie zrzutu Dr. Watson.  
  
- Edytowanie kodu po nieobsługiwanym wyjątku, gdy opcja **odwinięcia stosu wywołań w przypadku nieobsługiwanych wyjątków** nie jest zaznaczona.  
  
- Debugowanie osadzonej aplikacji środowiska uruchomieniowego.  
  
- Debugowanie aplikacji za pomocą **dołączania** zamiast uruchamiania aplikacji z menu **Start** z okna **debugowanie** .  
  
- Debugowanie zoptymalizowanego kodu.  
  
- Debugowanie kodu zarządzanego, gdy element docelowy jest aplikacją 64-bitową. Jeśli chcesz użyć opcji Edytuj i Kontynuuj, musisz ustawić wartość docelową na x86. (_Project_**Właściwości**projektu, karta **kompilacja** , **Zaawansowane ustawienie kompilatora** ).  
  
- Debugowanie starej wersji kodu od momentu kompilacji nowej wersji nie powiodło się z powodu błędów kompilacji.  
  
### <a name="to-edit-code-in-break-mode"></a>Aby edytować kod w trybie przerwania  
  
1. Przejdź do trybu przerwania, wykonując jedną z następujących czynności:  
  
    - Ustaw punkt przerwania w kodzie, a następnie wybierz **Rozpocznij debugowanie** z menu **Debuguj** i poczekaj, aż aplikacja osiągnie punkt przerwania.  
  
         oraz  
  
    - Rozpocznij debugowanie, a następnie wybierz polecenie **Przerwij wszystko** w menu **Debuguj** .  
  
         oraz  
  
    - Gdy wystąpi wyjątek, wybierz pozycję **Włącz edytowanie** w**Asystencie wyjątków**.  
  
2. Wprowadź odpowiednie i prawne zmiany kodu.  
  
     Aby uzyskać więcej informacji, zobacz [Nieobsługiwane edycje w Visual Basic Edytuj i Kontynuuj](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    > Jeśli spróbujesz wprowadzić zmianę kodu, która nie jest dozwolona przez edytowanie i kontynuowanie, Edycja zostanie podkreślona purpurową linią falistą i zostanie wyświetlone zadanie w Lista zadań. Nie będzie można kontynuować wykonywania kodu, chyba że zostanie cofnięta niedozwolona zmiana kodu.  
  
3. W menu **debugowanie** kliknij pozycję **Kontynuuj** , aby wznowić wykonywanie.  
  
     Kod jest teraz wykonywany z zastosowaniem zmian wprowadzonych w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Nieobsługiwane edycje w Visual Basic Edytuj i Kontynuuj](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
