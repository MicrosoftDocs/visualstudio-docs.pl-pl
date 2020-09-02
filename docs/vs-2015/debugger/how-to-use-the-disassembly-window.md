---
title: 'Instrukcje: korzystanie z okna demontażu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
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
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c25c3cdeb96abacb4123b2d0a851ac3d4acb0cd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696146"
---
# <a name="how-to-use-the-disassembly-window"></a>Porady: korzystanie z okna dezasemblacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja jest dostępna tylko wtedy, gdy debugowanie na poziomie adresu jest włączone okno dialogowe **Opcje** , **debugowanie** węzła. Nie jest dostępna w przypadku debugowania skryptów i SQL.  
  
 Okno **demontażu** zawiera kod zestawu odpowiadający instrukcjom utworzonym przez kompilator. Jeśli debugujesz kod zarządzany, te instrukcje zestawu odpowiadają kodowi natywnym utworzonym przez kompilator just-in-Time (JIT), a nie języka pośredniego firmy Microsoft (MSIL) generowanego przez kompilator programu Visual Studio.  
  
 Oprócz instrukcji zestawu, w oknie **demontażu** można wyświetlić następujące informacje opcjonalne:  
  
- Adres pamięci, w którym znajduje się każda instrukcja. W przypadku aplikacji natywnych jest to rzeczywisty adres pamięci. W przypadku Visual Basic, C# lub kodu zarządzanego, jest przesunięcie od początku funkcji.  
  
- Kod źródłowy, z którego pochodzi kod zestawu.  
  
- Bajty kodu — reprezentacje o rzeczywistej maszynie lub instrukcji MSIL.  
  
- Nazwy symboli dla adresów pamięci.  
  
- Numery wierszy odpowiadające kodowi źródłowej.  
  
  Instrukcje dotyczące języka asemblerowego składają się z symboli, które są skrótami nazw instrukcji i symboli, które reprezentują zmienne, rejestry i stałe. Każda instrukcja języka maszynowego jest reprezentowana przez jeden z języków asemblera, zwykle po którym następuje jedna lub więcej zmiennych, rejestrów lub stałych.  
  
  Jeśli nie możesz odczytać języka zestawu i chcesz w pełni skorzystać z okna demontażu, zapoznaj się z dobrą książką w zakresie programowania w języku asemblera. Programowanie języka zestawu jest poza zakresem tego, co możemy zająć w tym krótkim wprowadzeniu do okna demontażu.  
  
  Ponieważ kod zestawu jest w dużym stopniu oparty na rejestrach procesora lub, w przypadku kodu zarządzanego, rejestry środowiska uruchomieniowego języka wspólnego, często warto użyć okna demontażowego w połączeniu z oknem rejestry, co pozwala na badanie zawartości rejestru.  
  
  Prawdopodobnie nigdy nie będziesz mieć potrzeby lub nie musisz wyświetlać instrukcji dotyczących kodu maszynowego w pierwotnej, numerycznej formie, a nie w języku asemblera. Jeśli jednak chcesz to zrobić, możesz użyć okna pamięci do tego celu lub wybrać polecenie kod bajty z menu skrótów w oknie demontażu.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Aby wyświetlić okno demontaż  
  
- W menu **debugowanie** wybierz opcję **Windows**, a następnie kliknij pozycję **odzestawu**.  
  
     Debuger musi być uruchomiony lub w trybie przerwania.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Aby włączyć lub wyłączyć informacje opcjonalne  
  
- Kliknij prawym przyciskiem myszy okno **demontaż** i ustaw lub wyczyść odpowiednie opcje w menu skrótów.  
  
     Żółta strzałka w lewym marginesie oznacza lokalizację bieżącego punktu wykonania. W przypadku kodu natywnego odnosi się to do licznika programu procesora CPU. Ta lokalizacja pokazuje następną instrukcję, która zostanie wykonana w programie.  
  
     Aby uzyskać więcej informacji, zobacz [stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Porady: korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)
