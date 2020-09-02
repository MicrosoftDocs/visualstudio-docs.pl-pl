---
title: 'Instrukcje: Włączanie i wyłączanie Edytuj i Kontynuuj | Microsoft Docs'
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
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689266"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Porady: włączanie i wyłączanie opcji edytuj i kontynuuj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wyłączyć lub włączyć opcję Edytuj i Kontynuuj w oknie dialogowym **Opcje** w czasie projektowania. Nie można zmienić tego ustawienia podczas debugowania.  
  
 Polecenie Edytuj i Kontynuuj działa tylko w kompilacjach debugowania. W przypadku natywnego języka C++ Edycja i kontynuowanie wymaga użycia opcji/INCREMENTAL.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć/wyłączyć funkcję Edytuj i Kontynuuj  
  
1. Otwórz stronę opcje debugowania (**Narzędzia/Opcje/debugowanie**).  
  
2. Przewiń w dół do kategorii **Edytuj i Kontynuuj** .  
  
3. Aby włączyć, zaznacz pole wyboru **Włącz edytowanie i kontynuowanie** . Aby wyłączyć, wyczyść pole wyboru.  
  
   > [!NOTE]
   > Jeśli IntelliTrace jest włączona i zbierasz zarówno zdarzenia IntelliTrace, jak i informacje o wywołaniu, funkcja Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Kliknij przycisk **OK**.  
  
   Aby uzyskać więcej informacji na temat tych opcji, zobacz [Ogólne, debugowanie, opcje](../debugger/general-debugging-options-dialog-box.md)— okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj](../debugger/edit-and-continue.md)
