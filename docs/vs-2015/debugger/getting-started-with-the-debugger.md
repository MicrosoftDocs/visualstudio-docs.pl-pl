---
title: Wprowadzenie z debugerem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202315"
---
# <a name="getting-started-with-the-debugger"></a>Wprowadzenie do debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio jest łatwy w użyciu w dowolnym języku. Tutaj pokażemy sposób debugowania prostego programu w języku C#, ale można zastosować te same kroki do kodu w innych językach, takich jak C++ i JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Debugowanie podstawowego projektu C#  
 Zacznijmy od prostej aplikacji konsolowej w języku C# (**plik/nowy/projekt**, a następnie wybierz pozycję **Visual C#** , a następnie wybierz pozycję **Aplikacja konsolowa**). Jeśli wcześniej nie pracowałeś z programem Visual Studio, zobacz [Przewodnik: tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Metoda **Main** po prostu dodaje 1 do zmiennej całkowitej 10 razy i drukuje wynik do konsoli:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Skompiluj ten kod w konfiguracji **debugowania** . Ta konfiguracja jest domyślnie ustawiona. Więcej informacji o konfiguracjach znajduje się w temacie [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
 Uruchom ten kod w debugerze, klikając pozycję **Debuguj/Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**). Aplikacja powinna zakończyć niemal natychmiast, dlatego nie można w rzeczywistości sprawdzić, czy wszystkie elementy zostały wydrukowane w oknie konsoli.  
  
 Można zatrzymać wykonywanie wystarczająco długo, aby wyświetlić okno konsoli przez ustawienie punktu przerwania, a następnie przechodzenie do przodu. Aby ustawić punkt przerwania, umieść kursor w `Console.WriteLine` wierszu i kliknij kolejno opcje **Debuguj/nowy punkt przerwania/funkcja**lub po prostu kliknij w lewym górnym rogu w tym samym wierszu. Punkt przerwania powinien wyglądać następująco:  
  
 ![Ustawianie punktu przerwania](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Aby uzyskać więcej informacji na temat punktów przerwania, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Sprawdzanie zmiennych  
 Debugowanie często polega na znalezieniu zmiennych, które nie zawierają wartości oczekiwanych w określonym punkcie. Pokażemy kilka sposobów na sprawdzenie zmiennych.  
  
 Rozpocznij debugowanie ponownie. Wykonywanie zostało zatrzymane przed wykonaniem `Console.WriteLine` kodu. Możesz to zrobić, przewołując z wyprzedzeniem (kliknij pozycję **Debuguj/przekroczenie** lub **F10**). W takim przypadku można wybrać opcję **Wkrocz** (**F11**) i uzyskać ten sam wynik. wyjaśnimy różnicę później. Linia z ostatnim nawiasem klamrowym metody powinna mieć kolor żółty. Sprawdź okno konsoli. Powinna zostać wyświetlona **10**.  
  
 Możesz umieścić wskaźnik myszy nad zmienną **testInt** , aby wyświetlić bieżącą wartość w etykietce danych.  
  
 ![DBG&#95;podstawowe wskazówki&#95;danych&#95;](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Tuż poniżej okna kod, powinny być **widoczne okna** **zmiennych, lokalne**i **czujka** . Te okna pokazują bieżące wartości zmiennych w czasie wykonywania. Zarówno zmienne **Autostart** , jak i **lokalne** pokażą **testInt** z wartością **10**.  
  
 ![Okno autowypełniane podczas debugowania](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Aby uzyskać więcej informacji na temat tych okien, zobacz [Autostarty i lokalne okna](../debugger/autos-and-locals-windows.md).  
  
 Zobaczmy, jak zmienia się wartość zmiennej w miarę przechodzenia przez program. Ustaw punkt przerwania w `testInt += 1;` wierszu i ponownie uruchom debugowanie. Powinieneś zobaczyć, że **testInt** w wartościach **lokalnych** i **autouzupełniania** to **0**, a **i to** **1**. W przypadku kontynuowania debugowania (**Debuguj/Kontynuuj**lub **Kontynuuj** na pasku narzędzi lub **F5**) można zobaczyć, że wartość **testInt** zmienia się na **1**, a następnie **2**itd. Po uzyskaniu jakichkolwiek zmian w tych zmianach Usuń punkt przerwania (**Debuguj/Przełącz punkt przerwania**lub kliknij go na marginesie) i Kontynuuj debugowanie. Jeśli chcesz usunąć wszystkie punkty przerwania, kliknij pozycję **Debuguj/Usuń wszystkie punkty przerwania**lub **naciśnij klawisze CTRL + SHIFT + F9**, a następnie kliknij przycisk **tak** w oknie dialogowym z pytaniem, czy **chcesz usunąć wszystkie punkty przerwania?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Przechodzenie do i przekroczenie wywołań funkcji  
 Można wykonać kod w instrukcji debugera (**krok po kroku**) lub wykonać kod, gdy debuger pomija funkcje (**Step over**), aby szybko uzyskać kod, który jest bardziej interesujący (kod funkcji jest nadal wykonywany). Można przełączać się między obiema metodami w ramach tej samej sesji debugowania.  
  
 Aby zobaczyć różnicę między **krokiem** i **przekroczeniem**, musimy dodać metodę, która jest wywoływana przez inną metodę. Dodaj metodę do aplikacji C# i Wywołaj ją z metody Main. Kod powinien wyglądać następująco:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Ustaw punkt przerwania w `Method1();` wywołaniu metody Main i Rozpocznij debugowanie. Po przerwaniu wykonywania kliknij pozycję **Debuguj/Wkrocz do** (lub **Przejdź do** paska narzędzi lub klawisza **F11**). Ponownie podziały wykonania przy pierwszym nawiasie klamrowym w Metoda1 ():  
  
 ![Krokowe wykonywanie kodu](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Zatrzymaj debugowanie i rozpocznij ponownie, a kiedy wykonywanie jest przerywane w punkcie przerwania, kliknij pozycję **Debuguj/Przekrocz** **(lub Przekrocz na** pasku narzędzi lub **F10**). Podziały wykonania ponownie o `Console.WriteLine("end");` .  
  
 Jeśli chcesz dowiedzieć się więcej na temat nawigowania po kodzie za pomocą debugera, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).
