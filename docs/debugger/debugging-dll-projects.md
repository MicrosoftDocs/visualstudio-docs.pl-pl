---
title: Debugowanie projektów DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c00740b31e5b9d7cc5678bfc248e673a57e59ccf
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305315"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debugowanie bibliotek DLL w programie Visual Studio (C#, C++, Visual Basic F#)

Biblioteka DLL (Biblioteka DLL) jest bibliotekę, która zawiera kod i dane, które mogą być używane przez więcej niż jedną aplikację. Możesz użyć programu Visual Studio do tworzenia, tworzenie, konfigurowanie i debugowanie bibliotek DLL. 

## <a name="create-a-dll"></a>Tworzenie biblioteki DLL

Następujące szablony projektów programu Visual Studio można utworzyć biblioteki DLL:

- C#, Visual Basic lub F# Biblioteka klas 
- C#lub Visual Basic, Windows Forms Biblioteka kontrolek (WCF) 
- C++ biblioteki dołączanej (dynamicznie DLL)

Aby uzyskać więcej informacji, zobacz [techniki debugowania MFC](../debugger/mfc-debugging-techniques.md).

Debugowanie biblioteki WCF jest podobne do debugowania biblioteki klas. Aby uzyskać więcej informacji, zobacz [kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/index).  

Biblioteka DLL jest zwykle wywołanie z innego projektu. Podczas debugowania projektu wywołującego, w zależności od konfiguracji biblioteki DLL można wkroczyć do i możliwe jest debugowanie kodu biblioteki DLL. 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Konfiguracja debugowania bibliotek DLL

Gdy używasz szablonu projektu programu Visual Studio do tworzenia aplikacji, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release kompilacji. Możesz zmienić te ustawienia, jeśli to konieczne. Aby uzyskać więcej informacji zobacz następujące artykuły:

- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Ustawienia dla projektu C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Porady: konfiguracji ustaw wartość Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>Set C++ DebuggableAttribute

Aby debuger dołączał do biblioteki DLL języka C++, kod C++ musi wysyłać właściwość `DebuggableAttribute`. 

**Aby ustawić `DebuggableAttribute`:**

1. Wybierz projekt DLL języka C++ w **Eksploratora rozwiązań** i wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. 
   
1. W **właściwości** okienku w obszarze **konsolidatora** > **debugowanie**, wybierz opcję **tak (/ ASSEMBLYDEBUG)** dla  **Zestaw do debugowania**. 

Aby uzyskać więcej informacji, zobacz [/assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute).  

### <a name="vxtskdebuggingdllprojectsexternal"></a> Ustaw lokalizacje plików DLL języka C/C++ 

Aby debugować zewnętrznej biblioteki DLL, projektu wywołującego musi być w stanie odnaleźć biblioteki DLL, jego [plik .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)i innych plików wymaga pliku DLL. Można utworzyć zadanie niestandardowej kompilacji, aby skopiować te pliki do usługi  *\<folderu projektu > \Debug* folderu wyjściowego, lub skopiować pliki istnieje ręcznie.

Dla projektów C/C++ można ustawić nagłówek i lokalizacje plików LIB na stronach właściwości projektu, nie zaś ich kopiowanie do folderu wyjściowego. 

**Aby ustawić C/C++ lokalizacje plików nagłówka, jak i LIB:**

1. Wybierz projekt DLL języka C/C++ w **Eksploratora rozwiązań** i wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. 
   
1. W górnej części **właściwości** okienku w obszarze **konfiguracji**, wybierz opcję **wszystkie konfiguracje**.
   
1. W obszarze **C/C++** > **ogólne** > **dodatkowe katalogi dołączenia**, określ folder zawierający pliki nagłówków.
   
1. W obszarze **konsolidatora** > **ogólne** > **dodatkowe katalogi bibliotek**, określ folder zawierający pliki LIB. 
   
1. W obszarze **konsolidatora** > **dane wejściowe** > **dodatkowe zależności**, określ pełną ścieżkę i nazwę pliku dla plików LIB.

1. Wybierz **OK**.

Aby uzyskać więcej informacji na temat ustawień projektu C++, zobacz [strony właściwości (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Tworzenie wersji debugowania  

Upewnij się, że tworzenie wersji debugowania biblioteki dll, przed rozpoczęciem debugowania. Aby debugować bibliotekę DLL, wywoływania aplikacji musi być w stanie znaleźć jego [plik .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) i innych plików wymaga pliku DLL. 

Można utworzyć zadania niestandardowej kompilacji, aby skopiować pliki DLL do Twojej  *\<wywoływania folderu projektu > \Debug* folderu wyjściowego, lub skopiować pliki istnieje ręcznie.

Upewnij się, że wywołania biblioteki DLL w jego bieżącej lokalizacji. To może wydawać się oczywiste, ale jeśli wywoływania aplikacji umożliwia znalezienie i ładuje inną kopię pliku DLL, debuger nigdy nie spowoduje osiągnięcie punktów przerwania, które można ustawić. 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Debuguj DLL  

Nie można uruchomić biblioteki DLL bezpośrednio. Musi ona zostać wywołana przez aplikację, zwykle *.exe* pliku. Aby uzyskać więcej informacji, zobacz [Utwórz i Zarządzaj projektami Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects). 

Aby debugować bibliotekę DLL, możesz [rozpocząć debugowanie aplikacji wywołującej](#vxtskdebuggingdllprojectsthecallingapplication), lub [debugowanie z projektu DLL](how-to-debug-from-a-dll-project.md) , określając jego aplikacji wywołującej. Można również użyć debugera [bezpośrednim](#vxtskdebuggingdllprojectstheimmediatewindow) można obliczyć wartości funkcji DLL lub metody w czasie projektowania, bez korzystania z aplikacji wywołującej.

Aby uzyskać więcej informacji, zobacz [wprowadzenie do debugera](getting-started-with-the-debugger.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Rozpocznij debugowanie aplikacji wywołującej

Aplikacja, która wywołuje bibliotekę DLL może być:  
  
- Aplikację na podstawie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu, w tym samym lub innego rozwiązania z biblioteki DLL.  
- Istniejącą aplikację, która została już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym.  
- Znajduje się w sieci web i dostępne za pośrednictwem adresu URL.  
- Aplikacja internetowa ze stroną sieci web, która osadza biblioteki DLL.  
  
Aby debugować bibliotekę DLL z aplikacji wywołującej, można wykonywać następujące czynności:  
  
- Otwórz projekt dla aplikacji wywołującej i Rozpocznij debugowanie wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając **F5**.  

  lub  

- Dołącz do aplikacji, która jest już wdrożona i uruchomiona na komputerze testowym lub produkcyjnym. Użyj tej metody dla bibliotek DLL w witrynach sieci Web lub aplikacji sieci web. Aby uzyskać więcej informacji, zobacz [porady: dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Przed rozpoczęciem debugowania aplikacji wywołującej, należy ustawić punkt przerwania w DLL. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md). Po osiągnięciu punktu przerwania DLL możesz przejrzeć kod, obserwując działanie w każdym wierszu. Aby uzyskać więcej informacji, zobacz [Przechodzenie do kodu w debugerze](../debugger/navigating-through-code-with-the-debugger.md).
  
Podczas debugowania, możesz użyć **modułów** okna, aby sprawdzić biblioteki dll i *.exe* pliki obciążenia aplikacji. Aby otworzyć **modułów** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **modułów**. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md). 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Użyj okna bezpośredniego  

Możesz użyć **bezpośrednie** okna, aby ocenić funkcje biblioteki DLL lub metody w czasie projektowania. **Bezpośrednie** okna odgrywa rolę aplikacji wywołującej. 

>[!NOTE]
>Możesz użyć **bezpośrednie** okna w czasie projektowania za pomocą większość typów projektów. Nie jest obsługiwana dla programu SQL, projekty sieci web lub skryptu.

Na przykład, aby przetestować metodę o nazwie `Test` w klasie `Class1`:

1. Mając otwarty projekt DLL otwierać **bezpośrednie** okna, wybierając **debugowania** > **Windows** > **bezpośrednie**lub naciskając **Ctrl**+**Alt**+**I**.  
   
1. Utwórz wystąpienie obiektu typu `Class1` , wpisując następujące C# możesz pisać kod w **bezpośrednie** okna i naciskając klawisz **Enter**. Ten kod zarządzany działa dla C# i Visual Basic odpowiednich zmianach składni:  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   W C#, wszystkie nazwy muszą być w pełni kwalifikowana. Wszelkie metody lub zmienne musi być w bieżącym zakresie i kontekście, gdy usługa językowa podejmuje próbę obliczenia wyrażenia.  
   
1. Przy założeniu, że `Test` ma jedną `int` parametru oceny `Test` przy użyciu **bezpośrednie** okna:  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   Wynik jest drukowany w **bezpośrednie** okna.  
   
1. Można kontynuować debugowanie `Test` umieszczenie znajdującym się w nim punkt przerwania, a następnie ponownie oceniając funkcję.  
   
   Punkt przerwania zostanie osiągnięty, a następnie możesz przejrzeć `Test`. Po zakończeniu realizacji `Test`, debuger będzie ponownie w trybie projektowania.

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debugowanie w trybie mieszanym  

Można napisać wywoływania aplikacji dla bibliotek DLL z kodu zarządzanego lub natywnego. Jeśli chcesz debugować oba aplikacji natywnej wywołuje zarządzanej biblioteki DLL, można włączyć zarówno debugery zarządzanego i natywnego we właściwościach projektu. Dokładne proces zależy od tego, czy chcesz rozpocząć debugowanie z projektu DLL lub wywoływania projektu aplikacji. Aby uzyskać więcej informacji, zobacz [porady: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md). 

Można również debugować natywną bibliotekę DLL z zarządzanego projektu wywołującego. Aby uzyskać więcej informacji, zobacz [sposób debugowania kodu zarządzanego i natywnego](how-to-debug-managed-and-native-code.md). 

## <a name="see-also"></a>Zobacz także  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Typy projektów w usłudze Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia dla projektu C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
