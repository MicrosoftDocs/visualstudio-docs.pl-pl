---
title: Obsługiwane zmiany kodu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a68ad4add5f8c08e00067c903d5ba3946ca14538
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797978"
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj dla języka Visual C++ obsługuje większość typów zmian w kodzie. Jednak niektóre zmiany nie można zastosować podczas wykonywania programu. Aby zastosować te zmiany, należy zatrzymać wykonywanie i utworzenie świeżego wersji kodu.  
  
 Zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) informacje na temat pracy z funkcją Edytuj i Kontynuuj dla języka C++ w programie Visual Studio.  
  
##  <a name="BKMK_Unsupported_changes"></a> Nieobsługiwane zmiany  
 Nie można zastosować następujące zmiany języka C/C++ podczas sesji debugowania:  
  
- Większość zmian wprowadzonych do danych globalnych lub statycznych.  
  
- Zmiany do plików wykonywalnych, które są kopiowane z innego komputera i nie utworzone lokalnie.  
  
- Zmiany typu danych, które mają wpływ na układ obiektu, takie jak elementy członkowskie danych klasy.  
  
- Dodawanie więcej niż 64 KB danych lub nowego kodu.  
  
- Dodawanie zmiennych, które wymagają konstruktora w momencie przed wskaźnik instrukcji.  
  
- Zmiany, które mają wpływ na kod, który wymaga czasu wykonywania inicjowania.  
  
- Dodawanie obsługi wyjątków w pewnych okolicznościach.  
  
- Zmiany w plikach zasobów.  
  
- Zmiany kodu w plikach tylko do odczytu.  
  
- Zmiany kodu bez odpowiedniego pliku PDB.  
  
- Zmiany do kodu, który nie ma obiektu pliku.  
  
  Jeśli wytwarzania jednego z tych zmian, a następnie próby zastosowania zmian w kodzie, błąd lub ostrzeżenie pojawia się w **dane wyjściowe** okna.  
  
- Edytuj i Kontynuuj nie aktualizuje bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej, wykonywanie jest kontynuowane przy użyciu starej wersji, a nie ostrzeżenie.  
  
##  <a name="BKMK_Unsupported_scenarios"></a> Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj dla języka C/C++ jest niedostępna w następujących scenariuszach debugowania:  
  
-   Debugowanie natywne aplikacje skompilowane z [/Zo (Rozszerzanie zoptymalizowane pod kątem debugowania)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
-   W wersjach programu Visual Studio przed Visual Studio 2015 Update 1, debugowaniu aplikacji Windows Store lub składniki. Począwszy od programu Visual Studio 2015 Update 1 można Edytuj i Kontynuuj w aplikacji Windows Store w języku C++ i aplikacji DirectX, ponieważ teraz obsługuje `/ZI` przełącznika kompilatora z `/bigobj` przełącznika. Możesz również użyć Edytuj i Kontynuuj z plikami binarnymi kompilowany przy użyciu `/FASTLINK` przełącznika.  
  
-   Debugowanie, Windows 98.  
  
-   Debugowanie trybu mieszanego (natywnego/zarządzanego).  
  
-   Debugowanie kodu JavaScript.  
  
-   Debugowanie SQL.  
  
-   Debugowanie plików zrzutu.  
  
-   Edytowanie kodu po wystąpieniu nieobsługiwanego wyjątku, gdy **Unwind na stosie wywołań dotycząca nieobsłużonych wyjątków** nie wybrano opcji.  
  
-   Debugowanie aplikacji przy użyciu **dołączyć do** zamiast uruchamiać aplikację, wybierając **Start** na **debugowania** menu.  
  
-   Debugowanie zoptymalizowanego kodu.  
  
-   Debugowanie starą wersję kodu po nowej wersji nie powiodło się skompilowanie z powodu błędów kompilacji.  
  
##  <a name="BKMK_Linking_limitations"></a> Ograniczenia łączenia  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opcje konsolidatora, które wyłączanie funkcji Edytuj i Kontynuuj  
 Następujące opcje konsolidatora wyłączanie funkcji Edytuj i Kontynuuj:  
  
-   Ustawienie **/OPT: REF**, **/OPT: ICF**, lub **/incremental: No** wyłącza Edytuj i kontynuuj następujące ostrzeżenie:  
  
     LINK: ostrzeżenie LNK4075: Ignorowanie/editandcontinue z powodu od  
  
     specyfikacja  
  
-   Ustawienie **/ORDER**, **/RELEASE**, lub **/FORCE** wyłącza Edytuj i Kontynuuj tego ostrzeżenia:  
  
     LINK: ostrzeżenie LNK4075: Ignorowanie/incremental z powodu/Option  
  
     specyfikacja  
  
-   Ustawienie dowolnej opcji, które uniemożliwia utworzenie pliku bazy danych (PDB) program wyłącza Edytuj i Kontynuuj nie szczególne ostrzeżenie.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> Automatyczne ponowne łączenie ograniczenia  
 Domyślnie Edytuj i Kontynuuj relinks program na końcu sesji debugowania, aby utworzyć plik wykonywalny aktualne.  
  
 Edytuj i Kontynuuj nie może ponownie połączyć program Jeśli debugujesz z lokalizacji innych niż oryginalnej lokalizacji kompilacji. Zostanie wyświetlony komunikat informujący, że należy ponownie skompilować ręcznie.  
  
 Edytuj i Kontynuuj nie odbudować bibliotek statycznych. W przypadku wprowadzenia zmian do biblioteki statycznej przy użyciu Edytuj i Kontynuuj, należy ręcznie ponownie skompilować aplikacje biblioteki i połącz ponownie go używać.  
  
 Edytuj i kontynuuj nie wywołuje niestandardowych kroków kompilacji. Jeśli program używa niestandardowych kroków kompilacji, można ponownie skompilować ręcznie, aby można było wywołać niestandardowe kroki kompilacji. W takim przypadku, można wyłączyć ponowne połączenie po wykonaniu Edytuj i kontynuuj, aby zapewnić, że zostaniesz poproszony o ponowną kompilację ręczną.  
  
 **Aby wyłączyć ponowne połączenie po wykonaniu Edytuj i Kontynuuj**  
  
1.  Na **debugowania** menu, wybierz **opcje i ustawienia**.  
  
2.  W **opcje** dialogowego **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** węzła.  
  
3.  Wyczyść **Połącz ponownie zmiany kodu po debugowaniu** pole wyboru.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> Ograniczenia prekompilowanego nagłówka  
 Domyślnie Edytuj i Kontynuuj wstępnie skompilowanych nagłówków obciążeń i procesów w tle, aby przyspieszyć przetwarzanie zmian w kodzie. Ładowanie prekompilowanych nagłówków wymaga alokacji pamięci fizycznej, który może być problemem, jeśli kompilacja przebiega na komputerze z ograniczoną ilością pamięci RAM. Można określić, jeśli może to być problem za pomocą Menedżera zadań Windows, aby określić ilość dostępnej pamięci fizycznej podczas debugowania. Jeśli ta liczba jest większa niż rozmiar prekompilowanych nagłówków, nie powinny wystąpić problemy w trybie Edytuj i kontynuuj. Jeśli ilość jest mniejsza niż rozmiar prekompilowanych nagłówków, można uniemożliwić Edytuj i Kontynuuj ładowaniu prekompilowanych nagłówków w tle.  
  
 **Można wyłączyć ładowania tła prekompilowanych nagłówków na potrzeby operacji Edytuj i Kontynuuj**  
  
1.  Na **debugowania** menu, wybierz **opcje i ustawienia**.  
  
2.  W **opcje** dialogowego **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** węzła.  
  
3.  Wyczyść **Zezwalaj na Prekompilowanie** pole wyboru.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> Agraniczenia atrybutów języka IDL  
 Edytuj i Kontynuuj nie jest generowany ponownie plików definicji (języka IDL) interfejsu. W związku z tym zmiany atrybutów pliku IDL nie zostaną odzwierciedlone, podczas debugowania. Aby zobaczyć efekt zmian atrybuty IDL, należy zatrzymać debugowanie i ponownie skompiluj aplikację. Edytuj i Kontynuuj nie generuje błąd lub ostrzeżenie Jeżeli zmieniono atrybuty IDL. Aby uzyskać więcej informacji, zobacz [atrybuty IDL](http://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)



