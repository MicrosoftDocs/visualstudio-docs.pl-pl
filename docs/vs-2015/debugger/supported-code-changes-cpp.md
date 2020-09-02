---
title: Obsługiwane zmiany kodu (C++) | Microsoft Docs
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
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f167b3e9d27145284defa2ff491bb9ce0085f2a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684912"
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj dla Visual C++ obsługuje większość typów zmian kodu. Jednak niektórych zmian nie można zastosować podczas wykonywania programu. Aby zastosować te zmiany, należy zatrzymać wykonywanie i utworzyć nową wersję kodu.  
  
 Zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) , aby uzyskać informacje na temat pracy z funkcją Edytuj i Kontynuuj dla języka C++ w programie Visual Studio.  
  
## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Nieobsługiwane zmiany  

Następujące zmiany C/C++ nie mogą zostać zastosowane podczas sesji debugowania:  
  
- Większość zmian w danych globalnych lub statycznych.  
  
- Zmiany w plikach wykonywalnych, które są kopiowane z innego komputera i nie zostały utworzone lokalnie.  
  
- Zmiany typu danych, które mają wpływ na układ obiektu, takie jak składowe danych klasy.  
  
- Dodanie więcej niż 64 KB bajtów nowego kodu lub danych.  
  
- Dodawanie zmiennych, które wymagają konstruktora w punkcie przed wskaźnikiem instrukcji.  
  
- Zmiany wpływające na kod wymagający inicjalizacji w czasie wykonywania.  
  
- Dodawanie programów obsługi wyjątków, w niektórych przypadkach.  
  
- Zmiany w plikach zasobów.  
  
- Zmiany w kodzie w plikach tylko do odczytu.  
  
- Zmiany kodu bez odpowiedniego pliku PDB.  
  
- Zmiany w kodzie, który nie ma pliku obiektu.  
  
Jeśli wprowadzisz jedną z tych zmian, a następnie spróbujesz zastosować zmiany kodu, w oknie **danych wyjściowych** zostanie wyświetlony komunikat o błędzie lub ostrzeżenie.  
  
- Edytuj i Kontynuuj nie aktualizuje bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej, wykonywanie jest kontynuowane ze starą wersją i nie zostanie wygenerowane ostrzeżenie.  
  
## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj dla języka C/C++ jest niedostępny w następujących scenariuszach debugowania:  
  
- Debugowanie natywnych aplikacji skompilowanych za pomocą [/zo (rozszerzanie zoptymalizowanego debugowania)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
- W wersjach programu Visual Studio wcześniejszych niż Visual Studio 2015 Update 1 Debuguj aplikacje lub składniki sklepu Windows. Począwszy od programu Visual Studio 2015 Update 1, możesz użyć opcji Edytuj i Kontynuuj w aplikacjach ze sklepu Windows w języku C++ i aplikacji DirectX, ponieważ teraz obsługuje `/ZI` przełącznik kompilatora z  `/bigobj` przełącznikiem. Można również użyć opcji Edytuj i Kontynuuj z plikami binarnymi skompilowanymi przy użyciu `/FASTLINK` przełącznika.  
  
- Debugowanie w systemie Windows 98.  
  
- Debugowanie w trybie mieszanym (natywnym/zarządzanym).  
  
- Debugowanie JavaScript.  
  
- Debugowanie SQL.  
  
- Debugowanie pliku zrzutu.  
  
- Edytowanie kodu po nieobsługiwanym wyjątku, gdy opcja **odwinięcia stosu wywołań w przypadku nieobsługiwanych wyjątków** nie jest zaznaczona.  
  
- Debugowanie aplikacji przy użyciu funkcji **Dołącz do** zamiast uruchamiania aplikacji, wybierając pozycję **Rozpocznij** w menu **Debuguj** .  
  
- Debugowanie zoptymalizowanego kodu.  
  
- Debugowanie starej wersji kodu od momentu kompilacji nowej wersji nie powiodło się z powodu błędów kompilacji.  
  
## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Ograniczenia łączenia  
  
### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opcje konsolidatora, które wyłączają funkcję Edytuj i Kontynuuj  
 Następujące opcje konsolidatora Wyłącz Edytuj i Kontynuuj:  
  
- Ustawienie **/OPT: ref**, **/OPT: ICF**lub **/Incremental: nie** wyłącza opcji Edytuj i Kontynuuj z następującym ostrzeżeniem:  
  
     LINK: Warning LNK4075 narzędzi KONSOLIDATORA: ignorowanie/EDITANDCONTINUE z powodu/OPT  
  
     specyfikacja  
  
- Ustawienie **/Order**, **/Release**lub **/Force** wyłącza opcję Edytuj i Kontynuuj z ostrzeżeniem:  
  
     LINK: Warning LNK4075 narzędzi KONSOLIDATORA: ignorowanie/INCREMENTAL z powodu Option  
  
     specyfikacja  
  
- Ustawienie dowolnej opcji, która uniemożliwia tworzenie pliku bazy danych programu (. pdb) wyłącza polecenie Edytuj i Kontynuuj bez określonego ostrzeżenia.  
  
### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Ograniczenia autokonsolidacji  
 Domyślnie polecenie Edytuj i Kontynuuj ponownie łączy program na końcu sesji debugowania, aby utworzyć aktualny plik wykonywalny.  
  
 Edytuj i Kontynuuj nie można połączyć się z programem, jeśli jest debugowany z lokalizacji innej niż oryginalna lokalizacja kompilacji. Zostanie wyświetlony komunikat z informacją, że należy ponownie skompilować ręcznie.  
  
 Edytuj i Kontynuuj nie kompiluje bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej przy użyciu funkcji Edytuj i Kontynuuj, musisz ręcznie skompilować bibliotekę i ponownie połączyć z nią aplikacje.  
  
 Edytuj i kontynuuj nie wywołuje niestandardowych kroków kompilacji. Jeśli program używa niestandardowych kroków kompilacji, można ponownie skompilować ręcznie, aby można było wywołać niestandardowe kroki kompilacji. W takim przypadku, można wyłączyć ponowne połączenie po wykonaniu Edytuj i kontynuuj, aby zapewnić, że zostaniesz poproszony o ponowną kompilację ręczną.  
  
 **Aby wyłączyć ponowne łączenie po przeprowadzeniu edycji i kontynuowania**  
  
1. W menu **debugowanie** wybierz **Opcje i ustawienia**.  
  
2. W oknie dialogowym **Opcje** w węźle **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** .  
  
3. Wyczyść pole wyboru **Połącz ponownie zmiany kodu po debugowaniu** .  
  
## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_Header_Limitations"></a> Ograniczenia prekompilowanego nagłówka  
 Domyślnie polecenie Edytuj i Kontynuuj ładuje i przetwarza prekompilowane nagłówki w tle w celu przyspieszenia przetwarzania zmian w kodzie. Ładowanie prekompilowanych nagłówków wymaga alokacji pamięci fizycznej, co może być problemem w przypadku kompilowania na komputerze z ograniczoną ilością pamięci RAM. Można określić, czy może to być problem przy użyciu Menedżera zadań systemu Windows do określenia ilości dostępnej pamięci fizycznej podczas debugowania. Jeśli ta liczba jest większa niż rozmiar prekompilowanych nagłówków, nie powinny wystąpić problemy w trybie Edytuj i kontynuuj. Jeśli ilość jest mniejsza niż rozmiar wstępnie skompilowanych nagłówków, można zapobiec ładowaniu prekompilowanych nagłówków w tle przez polecenie Edytuj i Kontynuuj.  
  
 **Aby wyłączyć ładowanie wstępnie skompilowanych nagłówków dla Edytuj i Kontynuuj**  
  
1. W menu **debugowanie** wybierz **Opcje i ustawienia**.  
  
2. W oknie dialogowym **Opcje** w węźle **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** .  
  
3. Wyczyść pole wyboru **Zezwalaj na wstępne Kompilowanie** .  
  
## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_Attribute_Limitations"></a> Ograniczenia atrybutów IDL  
 Edytuj i Kontynuuj nie generuj ponownie plików definicji interfejsu (IDL). W związku z tym zmiany atrybutów IDL nie zostaną odzwierciedlone podczas debugowania. Aby zobaczyć wynik zmian atrybutów IDL, należy zatrzymać debugowanie i ponownie skompilować aplikację. Edytuj i Kontynuuj nie generuje błędu lub ostrzeżenia, jeśli atrybuty IDL zostały zmienione. Aby uzyskać więcej informacji, zobacz [atrybuty IDL](https://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
