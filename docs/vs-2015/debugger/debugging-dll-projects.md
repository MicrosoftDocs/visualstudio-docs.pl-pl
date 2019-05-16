---
title: Debugowanie projektów DLL | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691398"
---
# <a name="debugging-dll-projects"></a>Debugowanie projektów DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następujące szablony tworzą biblioteki DLL:  
  
- (C++, C# i Visual Basic) Biblioteka klas  
  
- (C++, C#i Visual Basic): Biblioteka formantów interfejsu Windows Forms  
  
   Debugowanie Biblioteka formantów Windows jest podobne do debugowania projektu biblioteki klas. W większości przypadków będzie wywoływać kontrolki Windows z innego projektu. Podczas debugowania projektu wywołującego można wkroczyć do kodu kontrolki Windows, ustawić punkty przerwania i wykonywać inne operacje debugowania. Aby uzyskać więcej informacji, zobacz [kontrolek formularzy Windows Forms](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# i Visual Basic): Biblioteka formantów sieci Web  
  
   Aby uzyskać więcej informacji, zobacz [Biblioteka formantów sieci Web (kod zarządzany)](../debugger/web-control-library-managed-code.md).  
  
- (C++): Formant ActiveX urządzeń inteligentnych MFC i formant ActiveX MFC  
  
   Formanty ActiveX to formanty, które można pobrane z Internetu na komputerze klienckim i wyświetlane oraz aktywowane na stronach sieci Web.  
  
   Debugowanie kontrolki ActiveX jest podobne do debugowania innych rodzajów formantów, ponieważ nie mogą być uruchamiane jako autonomiczne, ale muszą być osadzone na stronie sieci Web w formacie HTML. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie kontrolki ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): Biblioteka DLL urządzeń inteligentnych MFC  
  
   Aby uzyskać więcej informacji, zobacz [techniki testowania MFC](../debugger/mfc-debugging-techniques.md).  
  
  Ta sekcja zawiera również informacje o następujących tematach:  
  
- [Instrukcje: Debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Instrukcje: Debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Ten temat zawiera poniższe sekcje, w których omówiono sposób przygotowania debugowania biblioteki klas:  
  
- [Tworzenie wersji debugowania](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Debugowanie w trybie mieszanym](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Zmiana konfiguracji domyślnych](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Sposoby debugowania DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Aplikacja wywołująca](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Formanty na stronie sieci Web](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Okno bezpośrednie](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Tworzenie wersji debugowania  
 Niezależnie od tego, jak rozpocząć debugowanie upewnij się, najpierw Tworzenie wersji debugowania biblioteki DLL, a następnie upewnij się, że wersja do debugowania znajduje się w lokalizacji, gdzie jej szuka go znaleźć. To może wydawać się oczywiste, ale Jeśli zapomnisz tego kroku, aplikacja może znaleźć inną wersję biblioteki DLL i ją załadować. Następnie program będzie kontynuował zastanawiasz się, dlaczego nigdy nie został osiągnięty punkt przerwania. Podczas debugowania, możesz sprawdzić, które biblioteki DLL program załadował, przez otwarcie debugera **modułów** okna. **Modułów** okno zawiera listę każdego pliku DLL lub EXE załadowana w debugowanym procesie. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md).  
  
 Aby debuger dołączał do kodu napisanego w języku C++, kod musi wysyłać właściwość `DebuggableAttribute`. Można dodać to w kodzie automatycznie przez powiązanie z [/assemblydebug](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) — opcja konsolidatora.  
  
## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debugowanie w trybie mieszanym  
 Aplikacja wywołująca, która wywołuje bibliotekę DLL można pisać w kodzie zarządzanym lub kodzie natywnym. Jeśli zarządzana biblioteka DLL jest wywoływana przez kod macierzysty i chcesz debugować oba, zarządzane i natywne debugery należy włączyć. Można wybrać w  **\<Projekt > strony właściwości** lub oknie dialogowym. Jak to zrobić, zależy od tego, czy rozpoczynasz debugowanie z projektu DLL lub wywoływania projektu aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).  
  
## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Zmiana konfiguracji domyślnych  
 Po utworzeniu projektu aplikacji konsolowej przy użyciu szablonu projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. Jeśli to konieczne, możesz zmienić te ustawienia. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [ustawienia projektu dla C# Debuguj konfiguracje](../debugger/project-settings-for-csharp-debug-configurations.md), [ustawienia projektu dla debugowania języka Visual Basic Konfiguracja](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), i [jak: Ustaw wartość Debug i Release konfiguracje](../debugger/how-to-set-debug-and-release-configurations.md).  
  
## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Sposoby debugowania DLL  
 Każdy z projektów w tej sekcji tworzy bibliotekę DLL. Nie można uruchomić biblioteki DLL bezpośrednio; musi zostać wywołany przez aplikację, zwykle EXE. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie projekty języka Visual C++](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Aplikacja wywołująca może spełniać dowolne spośród następujących kryteriów:  
  
- Aplikacja utworzona w innym projekcie, w tym samym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które zawiera bibliotekę klas.  
  
- Istniejącą aplikację już wdrożona na komputerze testowym lub produkcyjnym.  
  
- Znajduje się w sieci Web i dostępne za pośrednictwem adresu URL.  
  
- Aplikacja sieci Web zawierającą stronę sieci Web, która osadza biblioteki DLL.  
  
### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugowanie aplikacji wywołującej  
 Aby debugować bibliotekę DLL, należy uruchomić debugowanie aplikacji wywołującej, zazwyczaj pliku EXE albo aplikacji sieci Web. Istnieje kilka sposobów jej debugowania.  
  
- Jeśli masz projekt dla aplikacji wywołującej, możesz otworzyć ten projekt i rozpocząć wykonywanie z **debugowania** menu. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie wykonywania](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Jeśli aplikacja wywołująca jest istniejący program już wdrożona na komputerze testowym lub produkcyjnym i działa już można dołączyć do niego. Użyj tej metody, jeśli biblioteka DLL jest formantem obsługiwanym przez program Internet Explorer lub formantem na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [jak: Dołączanie do uruchomionego procesu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Można to debugować z projektu DLL. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Można to debugować z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **bezpośrednie** okna. W tym przypadku **bezpośrednie** okna odgrywa rolę aplikacji.  
  
  Przed rozpoczęciem debugowania aplikacji wywołującej, zazwyczaj można ustawić punkt przerwania w bibliotece klas. Aby uzyskać więcej informacji, zobacz [punkty przerwania i śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Po osiągnięciu punktu przerwania można przechodzić przez kod, obserwując działanie w każdym wierszu, dopóki nie można ustalić przyczynę problemu. Aby uzyskać więcej informacji, zobacz [Przegląd przechodzenie krok po kroku kodu](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
### <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Formanty na stronie sieci Web  
 Aby debugować formant strony sieci Web, należy utworzyć [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strona, która ją osadza, jeśli taka strona jeszcze nie istnieje. Następnie umieścić punkty przerwania w kodzie strony sieci Web, a także w kodzie sterującym. Następnie wywołaj stronę sieci Web z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Przed rozpoczęciem debugowania aplikacji wywołującej, zazwyczaj można ustawić punkt przerwania w DLL. Po osiągnięciu punktu przerwania można przechodzić przez kod, obserwując działanie w każdym wierszu, dopóki nie można ustalić przyczynę problemu. Aby uzyskać więcej informacji, zobacz [punkty przerwania i śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Okno bezpośrednie  
 Będziesz w stanie ocenić funkcje lub metody w DLL bez wywoływana aplikacji. Możesz zrobić, debugowanie w czasie projektowania i używasz **bezpośrednie** okna. Aby debugować w ten sposób, wykonaj następujące kroki, podczas gdy projekt DLL jest otwarty:  
  
1. Otwórz narzędzie Debugger **bezpośrednie** okna.  
  
2. Aby przetestować metodę o nazwie `Test` w klasie `Class1`, tworzenia wystąpienia obiektu typu `Class1` , wpisując następujący kod C# w oknie bezpośrednim. Ten kod zarządzany działa dla języka Visual Basic i C++ po odpowiednich zmianach składni:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     W języku C# wszystkie nazwy muszą być w pełni kwalifikowana. Ponadto wszelkie metody lub zmienne muszą być w bieżącym zakresie i kontekście sesji debugowania.  
  
3. Przy założeniu, że `Test` ma jedną `int` parametru oceny `Test` przy użyciu **bezpośrednie** okna:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Wynik zostanie wydrukowany w **bezpośrednie** okna.  
  
4. Można kontynuować debugowanie `Test` umieszczając znajdującym się w nim punkt przerwania, a następnie ponownie oceniając funkcję:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Punkt przerwania zostanie osiągnięty i będzie można krokowo `Test`. Po zakończeniu realizacji `Test`, debuger będzie ponownie w trybie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
