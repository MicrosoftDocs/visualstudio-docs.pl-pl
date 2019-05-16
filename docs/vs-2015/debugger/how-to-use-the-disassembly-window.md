---
title: 'Instrukcje: Korzystanie z okna dezasemblacji | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696146"
---
# <a name="how-to-use-the-disassembly-window"></a>Instrukcje: Korzystanie z okna dezasemblacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja jest dostępna tylko wtedy, gdy włączone jest debugowanie na poziomie adresów **opcje** okno dialogowe **debugowanie** węzła. Nie jest dostępna do debugowania skryptów lub SQL.  
  
 **Dezasemblacji** okno pokazuje kod zestawu odpowiadający instrukcjom utworzonym przez kompilator. Jeśli debugujesz kod zarządzany w instrukcjach zestawu odnoszą się do kodu macierzystego, utworzony przez kompilator Just-in-Time (JIT), a nie języka Microsoft intermediate language (MSIL) generowany przez kompilator programu Visual Studio.  
  
 Oprócz instrukcje montażu **dezasemblacji** okna można wyświetlić następujące informacje opcjonalne:  
  
- Adres pamięci, w którym znajduje się każdą instrukcję. Dla natywnych aplikacji jest to adres pamięci rzeczywistych. W przypadku języka Visual Basic, C# lub kodu zarządzanego jest przesunięcie od początku funkcji.  
  
- Kod źródłowy, z którego pochodzi kod zestawu.  
  
- Bajty kodu — bajtów reprezentujących rzeczywistą lub instrukcji MSIL.  
  
- Nazwy symboli dla adresów pamięci.  
  
- Numery wierszy odpowiadających do kodu źródłowego.  
  
  Instrukcje języka asemblera składają się z klawiszy skrótu skrótów dla instrukcji nazwy i symbole, które reprezentują zmiennych, rejestrów i stałe. Każdą instrukcję języka maszyny jest reprezentowany przez jeden język asemblera skrót klawiszowy, zwykle następuje jeden lub więcej zmiennych, rejestrów lub stałe.  
  
  Jeśli nie można odczytać języka asembler i chcesz w pełni korzystać z okna dezasemblacji, zapoznaj się z dobrej książki na programowania języka asemblera. Język asemblera programowania jest poza zakres, w jaki firma Microsoft adres, w tym krótkie wprowadzenie do okna dezasemblacji.  
  
  Ponieważ kod zestawu rolę odgrywa w rejestrach procesora lub, w przypadku kodu zarządzanego, rejestruje środowiska uruchomieniowego języka wspólnego, użytkownik będzie często przydatne może użyć okna dezasemblacji w połączeniu z okna rejestrów, dzięki czemu można zbadać rejestr zawartość.  
  
  Prawdopodobnie będzie nigdy nie masz pragnienie lub konieczne wyświetlenie kodu maszynowego instrukcje w ich pierwotne, numerycznego formularza, a nie języka asemblera. Jednak jeśli chcesz to zrobić, możesz użyć okna pamięci, w tym celu lub wybrać bajty kodu z menu skrótów w oknie demontażu.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Aby wyświetlić okno dezasemblacji  
  
- Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **dezasemblacji**.  
  
     Debuger musi być uruchomiona lub w trybie przerwania.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Aby włączyć informacje opcjonalne lub wyłączyć  
  
- Kliknij prawym przyciskiem myszy **dezasemblacji** oknie i ustawić lub wyczyścić odpowiednie opcje w menu skrótów.  
  
     Żółta strzałka na lewym marginesie oznacza lokalizację bieżący punkt wykonania. Dla kodu natywnego odpowiada to licznik programu procesora CPU. Ta lokalizacja zawiera następnej instrukcji, która zostanie wykonana w programach.  
  
     Aby uzyskać więcej informacji, zobacz [stronicowanie w górę lub w dół w pamięci](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Instrukcje: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)
