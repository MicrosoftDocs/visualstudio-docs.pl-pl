---
title: Strona kompilacji, Projektant projektu (C#)
ms.date: 06/20/2017
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: eea14ebd5e4c56b62054a982aef83c1b8964b662
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650336"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)
Użyj **kompilacji** strony **projektanta projektu** do określania właściwości konfiguracji kompilacji projektu. Ten temat dotyczy [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] wyłącznie dla projektów.

Aby uzyskać dostęp do **kompilacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **widoku**, **stron właściwości** w menu. Gdy pojawi się w Projektancie projektu, wybierz **kompilacji** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma
Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. Dlatego te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [jak: Zestaw debugowania i zwalniania konfiguracji](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfiguracja** określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Te ustawienia mogą mieć **aktywna (debugowanie)** (to jest wartość domyślna), **debugowania**, **wersji**, lub **wszystkie konfiguracje**.

**Platforma** określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawieniem domyślnym jest **aktywna (dowolny procesor CPU)**. Możesz zmienić aktywną platformę przy użyciu **programu Configuration Manager**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne
Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.

**Symbole kompilacji warunkowej** określa symbole, na którym ma zostać wykonana zostanie kompilacja warunkowa. Oddziel symbole średnikiem (";"). Aby uzyskać więcej informacji, zobacz [/ define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Zdefiniuj stałą DEBUG** definiuje DEBUG jako symbol w kodzie źródłowym wszystkich plików w aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:DEBUG` opcji wiersza polecenia.

**Zdefiniuj stałą TRACE** definiuje TRACE jako symbol w kodzie źródłowym wszystkich plików w aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:TRACE` opcji wiersza polecenia.

**Platforma docelowa** Określa procesor, która ma zostać użyty przez plik wyjściowy. Wybierz **x86** dla dowolnej 32-bitowym procesorze zgodnego z Intel, wybierz **x64** dla dowolnego 64-bitowy procesor zgodnego z Intel, wybierz **ARM** dla procesorów ARM lub wybierz  **Dowolny procesor CPU** do określenia, czy akceptowalny jest każdy procesor. **Dowolny procesor CPU** jest wartością domyślną dla projektów, ponieważ umożliwia aplikacji, aby działała na najszerszym zakresie sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Preferuj 32-bitowe** Jeśli **Preferuj 32 bitowe** pole wyboru jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. Jeśli pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows.

W przypadku uruchomienia aplikacji jako aplikacji 64-bitowej podwaja się rozmiar wskaźnika, i z innych bibliotek, które są wyłącznie 32-bitowe, mogą wystąpić problemy ze zgodnością. Jest to przydatne do uruchamiania aplikacji 64-bitowych, tylko wtedy, gdy potrzebuje więcej niż 4 GB pamięci lub 64-bitowe instrukcje stanowią istotnie poprawiającą wydajność.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

-   Na **Stroka kompilacji**, **platformę docelową** listy jest ustawiona na **dowolny Procesor**.

-   Na **strony aplikacji**, **typ danych wyjściowych** lista określa, że projekt jest aplikacją.

-   Na **strony aplikacji**, **platformę docelową** lista określa .NET Framework 4.5.

**Zezwalaj na niebezpieczny kod** umożliwia kod, który używa [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) — słowo kluczowe, aby skompilować. Aby uzyskać więcej informacji, zobacz [/ unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optymalizuj kod** Włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne. Aby uzyskać więcej informacji, zobacz [/ optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia
Poniższe ustawienia są używane do skonfigurowania opcji błędów i ostrzeżeń dla procesu kompilacji.

**Poziom ostrzeżeń** określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/ warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Pomijanie ostrzeżeń** blokuje zdolność kompilatora do generowania co najmniej jedno ostrzeżenie. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy
Poniższe ustawienia są używane do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z poniższych opcji, aby wskazać, pod jakimi warunkami ma zostać zwrócony błąd, jeśli kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Brak** nie traktuje ostrzeżeń jako błędy.

**Określone ostrzeżenia** traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.

**Wszystkie** traktuje wszystkie ostrzeżenia jako błędy.

## <a name="output"></a>Dane wyjściowe
Następujące ustawienia są używane do skonfigurowania opcji wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa** Określa położenie plików wyjściowych dla tej konfiguracji projektu. Wprowadź ścieżkę produktu kompilacji w tym polu lub wybierz **Przeglądaj** przycisk, aby określić ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, jego zostanie zapisana jako względna. Domyślna ścieżka to bin\Debug lub bin\Release\\.

Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. **Kompilacji** polecenia **debugowania** menu (F5) umieszcza kompilację w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **kompilacji** polecenia **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika. Aby uzyskać więcej informacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md).

**Plik dokumentacji XML** Określa nazwę pliku do dokumentacji, które będą przetwarzane komentarze. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Zarejestruj dla współdziałania COM** wskazuje, że Twoją zarządzaną aplikacją udostępni obiektu COM (wywołalne opakowanie COM), który umożliwia obiektu COM na interakcję z Twoją zarządzaną aplikacją. **Typ danych wyjściowych** właściwość [strony aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) z **projektanta projektu** dla tej aplikacji musi być równa **biblioteki klas** w kolejność dla **Zarejestruj dla współdziałania COM** aby była dostępna właściwość. Aby uzyskać przykładową klasę, którą można umieścić w swojej [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] aplikacji i udostępniać jako obiekt COM, zobacz [klasa COM — przykład](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generuj zestaw serializacji** Określa, czy kompilator będzie używał narzędzie generatora serializatora XML (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania klasy <xref:System.Xml.Serialization.XmlSerializer> Jeśli ta klasa jest używana do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na **automatycznie**, która określa, że zestawy serializacji będą generowane tylko wtedy, gdy używasz <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do XML. **Wyłącz** Określa, że zestawy serializacji nigdy nie są generowane, niezależnie od tego, czy kod używa <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, że zestawy serializacji zawsze będą generowane. Zestawy serializacji noszą `TypeName`. XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatora XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowane** kliknij, aby wyświetlić [zaawansowane kompilacji okno dialogowe Ustawienia (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okno dialogowe.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)