---
title: Wprowadzenie do debugera | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202315"
---
# <a name="getting-started-with-the-debugger"></a>Wprowadzenie do debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio jest łatwa w użyciu w dowolnym języku. Tutaj pokażemy sposób debugowania prostego programu C#, ale te same kroki można stosować do kodu w innych językach, takich jak C++ i JavaScript.  
  
## <a name="BKMK_Start_debugging_a_VS_project"></a> Debugowanie projektu podstawowe języka C#  
 Zacznijmy od prostej aplikacji konsoli języka C# (**plik / nowy / Project**, a następnie wybierz **Visual C#** , a następnie wybierz **aplikację Konsolową**). Jeśli nigdy nie Pracowałem przy użyciu programu Visual Studio przed [instruktażu: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). **Main** metoda po prostu dodaje 1 na zmienną całkowitoliczbową 10 razy i drukuje wynik do konsoli:  
  
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
  
 Utwórz ten kod w **debugowania** konfiguracji. Ta konfiguracja jest ustawieniem domyślnym. Aby uzyskać więcej informacji o konfiguracji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).  
  
 Uruchom ten kod w debugerze, klikając pozycję **debugowania / uruchamiania debugowania** (lub **Start** na pasku narzędzi lub **F5**). Tak naprawdę nie można sprawdzić, czy wszystko zostało zrealizowane w oknie konsoli, aplikacji powinno powodować wyjście niemal natychmiast.  
  
 Zatrzymaj wykonywanie wystarczająco długi, tak aby wyświetlić okno konsoli przez ustawienie punktu przerwania i następnie krok naprzód. Aby ustawić punkt przerwania, umieść kursor `Console.WriteLine` wiersza, a następnie kliknij przycisk **debugowanie / nowy punkt przerwania / przerwania funkcji**, lub po prostu kliknij na lewym marginesie, w tym samym wierszu. Punkt przerwania powinien wyglądać następująco:  
  
 ![Ustaw punkt przerwania](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Aby uzyskać więcej informacji na temat punktów przerwania, zobacz [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
## <a name="BKMK_Inspect_Variables"></a> Sprawdzanie zmiennych  
 Debugowanie często polega na znajdowaniu zmiennych, które nie zawierają wartości, których oczekujesz, że w określonym punkcie. W tekście objaśniono niektóre metody, można sprawdzić zmiennych.  
  
 Uruchom ponownie debugowanie. Wykonanie zatrzymuje się przed `Console.WriteLine` kod jest wykonywany. Może spowodować, że wykonanie przez przechodzenie do przodu (kliknij **debugowanie / krok Over** lub **F10**). W takim przypadku może wybrano **Step Into** (**F11**) i uzyskać ten sam wynik; wyjaśnimy różnica później. Wiersz z ostatni nawias klamrowy metody powinny włączyli żółty. Spójrz na okno konsoli. Powinien zostać wyświetlony **10**.  
  
 Możesz umieścić kursor **testInt** zmiennej, aby wyświetlić bieżącą wartość w oknie z poradami danych.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Tuż poniżej oknie Kod powinien zostać wyświetlony **Autos**, **lokalne**, i **Obejrzyj** systemu windows. Te okna, Pokaż bieżące wartości zmiennych w czasie wykonywania. Zarówno **Autos** i **lokalne** Pokaż windows **testInt** o wartości **10**.  
  
 ![Okno zmiennych automatycznych podczas debugowania](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Aby uzyskać więcej informacji na temat tych okien, zobacz [zmiennych automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).  
  
 Zobaczmy, jak zmienia się wartość zmiennej jako części omówimy program. Ustaw punkt przerwania na `testInt += 1;` wiersza i uruchom ponownie debugowanie. Powinien zostać wyświetlony, który **testInt** w **lokalne** i **Autos** systemu windows jest **0**, i **i** jest **1**. Gdy Kontynuuj debugowanie (**debugowanie / Continue**, lub **Kontynuuj** na pasku narzędzi lub **F5**), możesz zobaczyć, że wartość **testInt** zmienia się na **1**, następnie **2**i tak dalej. Po otrzymaniu gdy spojrzenie na te zmiany, Usuń punkt przerwania (**debugowanie / Przełącz punkt przerwania**, lub kliknąć na marginesie) i Kontynuuj debugowanie. Jeśli chcesz usunąć wszystkie punkty przerwania, kliknij przycisk **debugowanie / Usuń wszystkie punkty przerwania**, lub **CTRL + SHIFT + F9**i kliknij przycisk **tak** w oknie dialogowym z pytaniem, **czy Czy chcesz usunąć wszystkie punkty przerwania?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Przechodzenie krok po kroku do, jak i za pośrednictwem wywołania funkcji  
 Można uruchamiać kod w instrukcji przez instrukcja debugera (**Step Into**) lub można wykonywać kod, gdy debuger pomija funkcji (**Step Over**) szybko w pełni do kodu, czy interesuje Cię bardziej () Kod funkcji jest nadal wykonywane). Możesz przełączać się między obu metod w tej samej sesji debugowania.  
  
 Aby zobaczyć różnicę między **Step Into** i **Step Over**, musimy dodać metodę, która jest wywoływana przy użyciu innej metody. Dodawanie metody do aplikacji C# i wywołać go z metody Main. Kod powinien wyglądać mniej więcej tak:  
  
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
  
 Ustaw punkt przerwania na `Method1();` wywołania metody Main, a następnie rozpocząć debugowanie. Kiedy przerywa wykonywanie, kliknij przycisk **debugowanie / Wkrocz** (lub **Step Into** na pasku narzędzi lub **F11**). Podziały wykonywania ponownie w pierwszym nawias klamrowy w method1() poprzez odwołanie:  
  
 ![Przechodzenie do kodu](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Zatrzymaj debugowanie, uruchom ponownie i kiedy przerywa wykonywanie w punkcie przerwania, kliknij przycisk **debugowanie / krok Over** (lub **Step Over** na pasku narzędzi lub **F10**). Wykonanie ponownie przerywa w `Console.WriteLine("end");`.  
  
 Jeśli chcesz dowiedzieć się więcej o nawigowanie po kodzie za pomocą debugera, zobacz [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md).
