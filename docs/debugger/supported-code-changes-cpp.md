---
title: Obsługiwane zmiany kodu (C++) | Microsoft Docs
description: Informacje o zmianach w kodzie, które są obsługiwane w przypadku korzystania z funkcji Edytuj i Kontynuuj podczas debugowania projektu C++ w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d000d2757321701c2e14427c6bbb4d3e4164d26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876306"
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C++)
Edytuj i Kontynuuj dla projektów C++ obsługuje większość typów zmian kodu. Jednak niektórych zmian nie można zastosować podczas wykonywania programu. Aby zastosować te zmiany, należy zatrzymać wykonywanie i utworzyć nową wersję kodu.

 Zobacz [Edytuj i Kontynuuj (C++)](../debugger/edit-and-continue-visual-cpp.md) , aby uzyskać informacje na temat pracy z funkcją Edytuj i Kontynuuj dla języka C++ w programie Visual Studio.

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Wymagania
### <a name="build-settings-project--properties"></a>Ustawienia kompilacji (właściwości > projektu):
  1. Język **C/C++ > ogólne > format informacji o debugowaniu**: programowej bazy danych do edycji i kontynuowania ( `/ZI` )
  2. **Generowanie kodu w języku C/C++ > > Włącz minimalną** ponowną kompilację: tak ( `/Gm` )
  3. **> łączący ogólne > Włącz konsolidację przyrostową**: tak ( `/INCREMENTAL` )

     Wszystkie niezgodne ustawienia konsolidatora (takie jak `/SAFESEH` , lub.. `/OPT:` .) powinny spowodować ostrzeżenia _LNK4075 narzędzi konsolidatora_ podczas kompilacji.  
     Przykład: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Ustawienia debugera (opcje > debugowania > ogólne):
  - Włącz natywną edycję i Kontynuuj

     Wszystkie niezgodne ustawienia kompilatora lub konsolidatora powodują wystąpienie błędu podczas edytowania i kontynuowania.  
     Przykład: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Nieobsługiwane zmiany
 Następujące zmiany w języku C/C++ nie mogą zostać zastosowane podczas sesji debugowania. Jeśli wprowadzisz dowolne z tych zmian, a następnie spróbujesz zastosować zmiany kodu, w oknie **danych wyjściowych** zostanie wyświetlony komunikat o błędzie lub ostrzeżenie.

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

* Modyfikowanie wyrażeń lambda, które:
  - Mieć statyczny lub globalny element członkowski.
  - Są przesyłane do funkcji std::. Powoduje to naruszenie oryginalnego naruszenia ODR i wyników w C1092.

- Edytuj i Kontynuuj nie aktualizuje bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej, wykonywanie jest kontynuowane ze starą wersją i nie zostanie wygenerowane ostrzeżenie.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Nieobsługiwane scenariusze
 Edytuj i Kontynuuj dla języka C/C++ jest niedostępny w następujących scenariuszach debugowania:

- Debugowanie natywnych aplikacji skompilowanych za pomocą [/zo (rozszerzanie zoptymalizowanego debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging)

- W wersjach programu Visual Studio wcześniejszych niż Visual Studio 2015 Update 1 Debuguj platformy UWP aplikacje lub składniki. Począwszy od programu Visual Studio 2015 Update 1, możesz użyć opcji Edytuj i Kontynuuj w aplikacjach platformy UWP C++ i DirectX Apps, ponieważ teraz obsługuje `/ZI` przełącznik kompilatora z  `/bigobj` przełącznikiem. Można również użyć opcji Edytuj i Kontynuuj z plikami binarnymi skompilowanymi przy użyciu `/FASTLINK` przełącznika.

- Debugowanie 8/8.1 aplikacji ze sklepu. Te projekty używają zestawu narzędzi VC 120 i przełącznika C/C++ `/bigobj` . Wartość Edytuj i Kontynuuj w programie `/bigobj` jest obsługiwana tylko w zestawie narzędzi VC 140.

- Debugowanie w systemie Windows 98.

- Debugowanie w trybie mieszanym (natywnym/zarządzanym).

- Debugowanie JavaScript.

- Debugowanie SQL.

- Debugowanie pliku zrzutu.

- Edytowanie kodu po nieobsługiwanym wyjątku, gdy opcja **odwinięcia stosu wywołań w przypadku nieobsługiwanych wyjątków** nie jest zaznaczona.

- Debugowanie aplikacji przy użyciu funkcji **Dołącz do** zamiast uruchamiania aplikacji, wybierając pozycję **Rozpocznij** w menu **Debuguj** .

- Debugowanie zoptymalizowanego kodu.

- Debugowanie starej wersji kodu od momentu kompilacji nowej wersji nie powiodło się z powodu błędów kompilacji.

- Użycie ścieżki niestandardowego kompilatora (*cl.exe*). Ze względów bezpieczeństwa na ponowną kompilację pliku podczas edytowania i kontynuowania program Visual Studio zawsze używa zainstalowanego kompilatora. Jeśli używasz niestandardowej ścieżki kompilatora (na przykład za pośrednictwem `$(ExecutablePath)` zmiennej niestandardowej w `*.props` pliku), wyświetlane jest ostrzeżenie, a program Visual Studio powraca do korzystania z zainstalowanego kompilatora o tej samej wersji/architekturze.

- System kompilacji FASTBuild. FASTBuild nie jest obecnie zgodne z przełącznikiem kompilatora "Włącz minimalną ponowną kompilację ( `/Gm` )", więc Edycja i kontynuacja nie są obsługiwane.

- Starsze architektury/zestawy narzędzi VC. Przy użyciu zestawu narzędzi VC 140 domyślny Debuger obsługuje edytowanie i kontynuowanie w przypadku aplikacji x86 i x64. Starsze zestawy narzędzi obsługują tylko aplikacje x86. Zestawy narzędzi starsze niż VC 120 powinny używać starszego debugera, sprawdzając "_opcje > debugowania > ogólne >_ użyć macierzystego trybu zgodności", aby użyć polecenia Edytuj i Kontynuuj.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Ograniczenia łączenia

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opcje konsolidatora, które wyłączają funkcję Edytuj i Kontynuuj
 Następujące opcje konsolidatora Wyłącz Edytuj i Kontynuuj:

- Ustawienie **/OPT: ref**, **/OPT: ICF** lub **/Incremental: nie** wyłącza opcji Edytuj i Kontynuuj z następującym ostrzeżeniem:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- Ustawienie **/Order**, **/Release** lub **/Force** wyłącza opcję Edytuj i Kontynuuj z następującym ostrzeżeniem:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

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

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Ograniczenia prekompilowanego nagłówka
 Domyślnie polecenie Edytuj i Kontynuuj ładuje i przetwarza prekompilowane nagłówki w tle w celu przyspieszenia przetwarzania zmian w kodzie. Ładowanie prekompilowanych nagłówków wymaga alokacji pamięci fizycznej, co może być problemem w przypadku kompilowania na komputerze z ograniczoną ilością pamięci RAM. Można określić, czy może to być problem przy użyciu Menedżera zadań systemu Windows do określenia ilości dostępnej pamięci fizycznej podczas debugowania. Jeśli ta liczba jest większa niż rozmiar prekompilowanych nagłówków, nie powinny wystąpić problemy w trybie Edytuj i kontynuuj. Jeśli ilość jest mniejsza niż rozmiar wstępnie skompilowanych nagłówków, można zapobiec ładowaniu prekompilowanych nagłówków w tle przez polecenie Edytuj i Kontynuuj.

 **Aby wyłączyć ładowanie wstępnie skompilowanych nagłówków dla Edytuj i Kontynuuj**

1. W menu **debugowanie** wybierz **Opcje i ustawienia**.

2. W oknie dialogowym **Opcje** w węźle **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** .

3. Wyczyść pole wyboru **Zezwalaj na wstępne Kompilowanie** .

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> Ograniczenia atrybutów IDL
 Edytuj i Kontynuuj nie generuj ponownie plików definicji interfejsu (IDL). W związku z tym zmiany atrybutów IDL nie zostaną odzwierciedlone podczas debugowania. Aby zobaczyć wynik zmian atrybutów IDL, należy zatrzymać debugowanie i ponownie skompilować aplikację. Edytuj i Kontynuuj nie generuje błędu lub ostrzeżenia, jeśli atrybuty IDL zostały zmienione. Aby uzyskać więcej informacji, zobacz [atrybuty IDL](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Diagnozowanie problemów
 Jeśli scenariusz nie pasuje do żadnego z powyższych warunków, można zebrać więcej szczegółów, ustawiając następującą wartość rejestru DWORD:
 1. Otwórz wiersz polecenia dla deweloperów.
 2. Uruchom następujące polecenie:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Ustawienie tej wartości na początku sesji debugowania powoduje, że różne składniki edytują i kontynuują Spew pełne rejestrowanie do   >  okienka **debugowania** okno dane wyjściowe.

## <a name="see-also"></a>Zobacz też
- [Edytuj i kontynuuj (C++)](../debugger/edit-and-continue-visual-cpp.md)
