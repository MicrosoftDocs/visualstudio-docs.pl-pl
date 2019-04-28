---
title: 'Instrukcje: Włącz i Wyłącz Edytuj i Kontynuuj | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d564162a92976037729c4ad638136d7c1e827c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438288"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Instrukcje: Włącz i Wyłącz Edytuj i Kontynuuj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wyłączyć lub włączyć Edytuj i Kontynuuj w **opcje** okno dialogowe, w czasie projektowania. Nie można zmienić tego ustawienia podczas debugowania.  
  
 Edytuj i Kontynuuj działa tylko w kompilacjach do debugowania. Dla natywnych języka C++, Edytuj i Kontynuuj wymaga przy użyciu / incremental — opcja.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć lub wyłączyć Edytuj i Kontynuuj  
  
1. Otwórz stronę opcji debugowania (**narzędzia / Opcje / Debugowanie**).  
  
2. Przewiń w dół do **Edytuj i Kontynuuj** kategorii.  
  
3. Aby włączyć, wybierz **Włącz edytowanie i kontynuowanie** pole wyboru. Aby wyłączyć, wyczyść pole wyboru.  
  
   > [!NOTE]
   > Jeśli zbieranie zdarzeń IntelliTrace i informacje o wywołaniach funkcji IntelliTrace jest włączony, Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [skonfigurować IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Kliknij przycisk **OK**.  
  
   Aby uzyskać więcej informacji o tych opcjach, zobacz [ogólne, debugowanie, okno dialogowe Opcje](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj](../debugger/edit-and-continue.md)
