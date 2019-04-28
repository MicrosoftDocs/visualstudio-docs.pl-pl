---
title: 'Instrukcje: Korzystanie z okna rejestrów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 506425f4de218e258ca9a86bfad5154cbda5c223
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445040"
---
# <a name="how-to-use-the-registers-window"></a>Instrukcje: Korzystanie z okna rejestrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe **debugowanie** węzła **ogólne** kategorii.  
  
 **Rejestruje** okna wyświetla zawartość rejestru. Jeśli zachowasz **rejestruje** otwarte, jak krok po kroku przez program okno, możesz zobaczyć zmiany wartości rejestru, jak kod jest wykonywany. Wartości, które zostały zmienione ostatnio są wyświetlane w kolorze czerwonym. Możesz edytować wartości rejestru. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie wartości rejestru](../debugger/how-to-edit-a-register-value.md).  
  
 Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach, które zależą od platformy i procesora typu. Można wyświetlić lub ukryć grup, jak chcesz. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie i ukrywanie grup rejestru](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Ogólne wprowadzenie do pojęć dotyczących rejestrów i z okna rejestrów, zobacz [podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Aby wyświetlić okno rejestrów  
  
- Na **debugowania** menu, wybierz **Windows**, a następnie wybierz **rejestruje**.  
  
     Debuger musi być uruchomiona lub w trybie przerwania.  
  
    > [!NOTE]
    > Informacje rejestru nie są dostępne dla skryptu lub aplikacji SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)
