---
title: Debugowanie projektów DLL | Microsoft Docs
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
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a4533c304f84d9dc59ec6b05328528870e49655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691398"
---
# <a name="debugging-dll-projects"></a>Debugowanie projektów DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące szablony tworzą biblioteki dll:  
  
- (C++, C# i Visual Basic) Biblioteka klas  
  
- (C++, C# i Visual Basic): Biblioteka formantów Windows Forms  
  
   Debugowanie Biblioteki formantów systemu Windows jest podobne do debugowania projektu biblioteki klas. W większości przypadków formant systemu Windows jest wywoływany z innego projektu. Gdy debugujesz projekt wywołujący, możesz przejść do kodu kontrolki systemu Windows, ustawić punkty przerwania i wykonać inne operacje debugowania. Aby uzyskać więcej informacji, zobacz [Windows Forms Controls](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# i Visual Basic): Biblioteka kontrolek sieci Web  
  
   Aby uzyskać więcej informacji, zobacz [Biblioteka kontrolek sieci Web (kod zarządzany)](../debugger/web-control-library-managed-code.md).  
  
- (C++): formant ActiveX MFC i Kontrolka ActiveX urządzenia inteligentnego MFC  
  
   Formanty ActiveX są kontrolkami, które można pobrać za pośrednictwem Internetu na komputer kliencki i wyświetlane i aktywowane na stronach sieci Web.  
  
   Debugowanie formantów ActiveX przypomina debugowanie innych rodzajów kontrolek, ponieważ nie mogą być uruchamiane jako autonomiczne, ale muszą być osadzone na stronie sieci Web w formacie HTML. Aby uzyskać więcej informacji, zobacz [How to: Debug The ActiveX Control](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): Biblioteka DLL urządzeń inteligentnych MFC  
  
   Aby uzyskać więcej informacji, zobacz [techniki debugowania MFC](../debugger/mfc-debugging-techniques.md).  
  
  Ta sekcja zawiera również informacje o następujących tematach:  
  
- [Instrukcje: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Instrukcje: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Ten temat zawiera następujące sekcje, które zawierają zagadnienia dotyczące przygotowania do bibliotek klas debugowania:  
  
- [Kompilowanie wersji do debugowania](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Debugowanie w trybie mieszanym](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Zmienianie konfiguracji domyślnych](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Sposoby debugowania biblioteki DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Aplikacja wywołująca](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Kontrolki na stronie sieci Web](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Okno bezpośrednie](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="building-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Kompilowanie wersji do debugowania  
 Niezależnie od tego, jak rozpoczynasz debugowanie, upewnij się, że najpierw kompilujesz wersję do debugowania biblioteki DLL i upewnij się, że wersja do debugowania znajduje się w lokalizacji, w której aplikacja oczekuje na jej znalezienie. Może wydawać się oczywiste, ale w przypadku zapomnienia tego kroku aplikacja może znaleźć inną wersję biblioteki DLL i załadować ją. Program będzie kontynuował pracę, ale zastanawiasz się, dlaczego punkt przerwania nigdy nie został trafiony. Podczas debugowania można sprawdzić, które biblioteki DLL zostały załadowane przez program, otwierając okno **modułów** debugera. W oknie **moduły** jest wyświetlana każda biblioteka DLL lub EXE załadowana w debugowanym procesie. Aby uzyskać więcej informacji, zobacz [How to: Use the modules Window](../debugger/how-to-use-the-modules-window.md).  
  
 Aby debuger dołączał do kodu pisanego w języku C++, kod musi emitować `DebuggableAttribute` . Możesz dodać to do kodu automatycznie, łącząc się z opcją konsolidatora [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .  
  
## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debugowanie w trybie mieszanym  
 Aplikacja wywołująca, która wywołuje bibliotekę DLL, może być zapisywana w kodzie zarządzanym lub kodzie macierzystym. Jeśli zarządzana Biblioteka DLL jest wywoływana przez kod natywny i chcesz debugować oba, należy włączyć zarówno debugery zarządzane, jak i natywne. Można wybrać tę opcję w oknie dialogowym ** \<Project> strony właściwości** lub w oknie. Jak to zrobić, zależy od tego, czy rozpoczynasz debugowanie z projektu DLL lub projektu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [jak: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).  
  
## <a name="changing-default-configurations"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Zmienianie konfiguracji domyślnych  
 Podczas tworzenia projektu aplikacji konsolowej przy użyciu szablonu projektu program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie tworzy wymagane ustawienia dla konfiguracji debugowania i wydania. W razie potrzeby możesz zmienić te ustawienia. Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md), [ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)i [instrukcje: Ustawianie konfiguracji debugowania i wersji](../debugger/how-to-set-debug-and-release-configurations.md).  
  
## <a name="ways-to-debug-the-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Sposoby debugowania biblioteki DLL  
 Każdy projekt w tej sekcji tworzy plik DLL. Nie można bezpośrednio uruchomić biblioteki DLL; musi być wywoływana przez aplikację, zazwyczaj jako plik WYKONYWALNy. Aby uzyskać więcej informacji, zobacz [Tworzenie projektów Visual C++ i zarządzanie nimi](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Aplikacja wywołująca może dopasować jedno z następujących kryteriów:  
  
- Aplikacja skompilowana w innym projekcie w tym samym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu, które zawiera bibliotekę klas.  
  
- Istniejąca aplikacja została już wdrożona na komputerze testowym lub produkcyjnym.  
  
- Znajdujący się w sieci Web i dostęp za pomocą adresu URL.  
  
- Aplikacja sieci Web, która zawiera stronę sieci Web, która osadza bibliotekę DLL.  
  
### <a name="debugging-the-calling-application"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugowanie aplikacji wywołującej  
 Aby debugować bibliotekę DLL, Zacznij od debugowania aplikacji wywołującej, zazwyczaj jest to plik WYKONYWALNy lub aplikacja sieci Web. Istnieje kilka sposobów na jego debugowanie.  
  
- Jeśli masz projekt dla aplikacji wywołującej, możesz otworzyć ten projekt i rozpocząć wykonywanie z menu **Debuguj** . Aby uzyskać więcej informacji, zobacz [How to: Start Execution](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Jeśli aplikacja wywołująca jest istniejącym programem już wdrożonym na komputerze testowym lub produkcyjnym i jest już uruchomiony, możesz dołączyć do niego. Tej metody należy użyć, jeśli biblioteka DLL jest formantem hostowanym przez program Internet Explorer lub formantem na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [jak: dołączanie do uruchomionego procesu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Można go debugować z projektu DLL. Aby uzyskać więcej informacji, zobacz [jak: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Można go debugować z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna **bezpośredniego** . W takim przypadku okno **bezpośrednie** odgrywa rolę aplikacji.  
  
  Przed rozpoczęciem debugowania aplikacji wywołującej, zazwyczaj należy ustawić punkt przerwania w bibliotece klas. Aby uzyskać więcej informacji, zobacz [punkty przerwania i punkty śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Po trafieniu punktu przerwania można przechodzić przez kod, obserwując akcję w poszczególnych wierszach, aż do odizolowania problemu. Aby uzyskać więcej informacji, zobacz [Omówienie wykonywania kodu](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
### <a name="controls-on-a-web-page"></a><a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Kontrolki na stronie sieci Web  
 Aby debugować formant strony sieci Web, należy utworzyć [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stronę, która osadza ją, jeśli taka strona jeszcze nie istnieje. Następnie umieść punkty przerwania w kodzie strony sieci Web, a także kod sterujący. Następnie Wywołaj stronę sieci Web z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Przed rozpoczęciem debugowania aplikacji wywołującej, zazwyczaj należy ustawić punkt przerwania w bibliotece DLL. Po trafieniu punktu przerwania można przechodzić przez kod, obserwując akcję w poszczególnych wierszach, aż do odizolowania problemu. Aby uzyskać więcej informacji, zobacz [punkty przerwania i punkty śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Okno bezpośrednie  
 Można oszacować funkcje lub metody w bibliotece DLL bez wywoływania aplikacji. Debugowanie w czasie projektowania i korzystanie z okna **bezpośredniego** . Aby debugować w ten sposób, wykonaj następujące kroki, gdy projekt DLL jest otwarty:  
  
1. Otwórz **natychmiastowe** okno debugera.  
  
2. Aby przetestować metodę o nazwie `Test` w klasie `Class1` , Utwórz wystąpienie obiektu typu `Class1` przez wpisanie poniższego kodu w języku C# w oknie bezpośrednim. Ten zarządzany kod działa dla Visual Basic i C++ z odpowiednimi zmianami składni:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     W języku C# wszystkie nazwy muszą być w pełni kwalifikowane. Ponadto wszelkie metody lub zmienne muszą znajdować się w bieżącym zakresie i kontekście sesji debugowania.  
  
3. Przy założeniu, że `Test` przyjmuje jeden `int` parametr, Oceń `Test` przy użyciu okna **bezpośredniego** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Wynik zostanie wydrukowany w oknie **bezpośrednim** .  
  
4. Możesz kontynuować debugowanie `Test` , umieszczając w niej punkt przerwania, a następnie ponownie oceniając funkcję:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Punkt przerwania zostanie trafiony i będzie można przejść do niego `Test` . Po `Test` powrocie wykonania debuger zostanie przywrócony do trybu projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Visual C++ typy projektów](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
