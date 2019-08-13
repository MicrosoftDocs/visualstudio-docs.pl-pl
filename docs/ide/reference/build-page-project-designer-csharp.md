---
title: Strona kompilacji, Projektant projektu (C#)
ms.date: 06/20/2017
ms.technology: vs-ide-compile
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
ms.openlocfilehash: 146d98701f144aacf0ff073c3099b2239ebd1872
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461454"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)

Użyj strony **kompilacja** **projektanta projektu** , aby określić właściwości konfiguracji kompilacji projektu. Ta strona ma zastosowanie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tylko do projektów.

Aby uzyskać dostęp do strony **kompilacja** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **Widok**, **strony właściwości** w menu. Gdy zostanie wyświetlony Projektant projektu, wybierz kartę **kompilacja** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. W związku z tym te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie konfiguracji](../../debugger/how-to-set-debug-and-release-configurations.md)debugowania i wydania.

**Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **aktywne (Debugowanie)** (jest to ustawienie domyślne), **debugowanie**, **wydanie**lub **wszystkie konfiguracje**.

**Platformach**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienie domyślne jest **aktywne (dowolny procesor)** . Możesz zmienić aktywną platformę przy użyciu **Configuration Manager**. Aby uzyskać więcej informacji, zobacz [jak: Utwórz i Edytuj konfiguracje](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają skonfigurowanie kilku C# ustawień kompilatora.

**Symbole kompilacji warunkowej**

Określa symbole, na których ma zostać wykonana Kompilacja warunkowa. Oddzielaj symbole średnikami (";"). Aby uzyskać więcej informacji, zobacz [/defineC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Zdefiniuj stałą DEBUG**

Definiuje debugowanie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoważne użyciu `/define:DEBUG` opcji wiersza polecenia.

**Zdefiniuj stałą TRACE**

Definiuje śledzenie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoważne użyciu `/define:TRACE` opcji wiersza polecenia.

**Obiekt docelowy platformy**

Określa procesor, który ma być przeznaczony dla pliku wyjściowego. Wybierz opcję **x86** dla dowolnego 32-bitowego procesora zgodnego z technologią Intel, wybierz **x64** dla dowolnego 64-bitowego procesora zgodnego z technologią Intel, wybierz pozycję **ARM** dla procesorów ARM lub wybierz **dowolny** procesor, aby określić, że każdy z procesorów jest akceptowalny. **Każdy procesor** jest wartością domyślną dla projektów, ponieważ umożliwia uruchamianie aplikacji na najszerszym zakresie sprzętu.

Aby uzyskać więcej informacji, zobacz [/platformC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Preferuj 32-bitowe**

Jeśli pole wyboru **Prefer32-bitowy** jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa na 32-bitowej i 64-bitowej wersji systemu Windows. Jeśli to pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bit w systemie 64-bitowe wersje systemu Windows.

Jeśli aplikacja jest uruchamiana jako aplikacja 64-bitowa, rozmiar wskaźnika podwaja się i problemy ze zgodnością mogą wystąpić w przypadku innych bibliotek, które są wyłącznie 32-bitowe. Warto uruchamiać aplikacje 64-bitowe tylko wtedy, gdy potrzebują więcej niż 4 GB pamięci lub instrukcje 64-bitowe zapewniają znaczący wzrost wydajności.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie kompilacja**na liście **docelowy platformy** jest ustawiona wartość **dowolny procesor CPU**.

- Na **stronie aplikacja**na liście **typ wyjścia** określa, że projekt jest aplikacją.

- Na **stronie aplikacja**lista **platform docelowych** określa .NET Framework 4,5.

**Zezwalaj na niebezpieczny kod**

Zezwala na kompilowanie kodu [niebezpieczny](/dotnet/csharp/language-reference/keywords/unsafe) , który używa niebezpiecznego słowa kluczowego. Aby uzyskać więcej informacji, zobacz [/UNSAFEC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optymalizuj kod**

Włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny. Aby uzyskać więcej informacji, zobacz [/OptimizeC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Poniższe ustawienia służą do konfigurowania opcji błędu i ostrzeżenia dla procesu kompilacji.

**Poziom ostrzeżeń**

Określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/warnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Pomiń ostrzeżenia**

Blokuje możliwość generowania co najmniej jednego ostrzeżenia przez kompilator. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Poniższe ustawienia służą do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z następujących opcji, aby wskazać, w których warunkach ma zostać zwrócony błąd, gdy kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserrorC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Brak**

Nie traktuje żadnych ostrzeżeń jako błędów.

**Określone ostrzeżenia**

Traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.

**Całą**

Traktuje wszystkie ostrzeżenia jako błędy.

## <a name="output"></a>Dane wyjściowe

Poniższe ustawienia służą do konfigurowania opcji danych wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa**

Określa lokalizację plików wyjściowych dla konfiguracji projektu. Wprowadź ścieżkę do danych wyjściowych kompilacji w tym polu lub wybierz przycisk **Przeglądaj** , aby określić ścieżkę. Ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie ona zapisana jako względna. Ścieżka domyślna to bin\Debug lub bin\Release\\.

W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. Polecenie **Build** z menu **Debuguj** (F5) umieści kompilację w lokalizacji debugowania niezależnie od określonej **ścieżki wyjściowej** . Jednak polecenie **Build** z menu **kompilacja** umieszcza je w określonej lokalizacji. Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

**Plik dokumentacji XML**

Określa nazwę pliku, do którego zostaną przetworzone komentarze dokumentacji. Aby uzyskać więcej informacji, zobacz [/docC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Rejestracja w celu współdziałania z modelem COM**

Wskazuje, że aplikacja zarządzana uwidacznia obiekt COM (otoka COM, która jest wywoływana), która umożliwia obiektowi COM współpracujące z zarządzaną aplikacją. Właściwość **Typ danych wyjściowych** na [stronie aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) **projektanta projektu** dla tej aplikacji musi być ustawiona na wartość **Biblioteka klas** , aby właściwość **register dla elementu com** była dostępna. Aby zapoznać się z przykładową klasą, którą [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] można uwzględnić w aplikacji i uwidocznić jako obiekt com, zobacz [przykład klasy com](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generuj zestaw serializacji**

Określa, czy kompilator będzie używać narzędzie XML Serializer Generator (Sgen. exe) do tworzenia zestawów serializacji XML. Zestawy serializacji mogą zwiększyć wydajność <xref:System.Xml.Serialization.XmlSerializer> uruchamiania, jeśli użyto tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na wartość **automatycznie**, co oznacza, że zestawy serializacji są generowane tylko wtedy, gdy używane <xref:System.Xml.Serialization.XmlSerializer> jest kodowanie typów w kodzie do formatu XML. **Wyłączone** określa, że zestawy serializacji nigdy nie są generowane, bez względu na to <xref:System.Xml.Serialization.XmlSerializer>, czy kod używa. **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji mają nazwę `TypeName`. XmlSerializers. dll. Aby uzyskać więcej informacji, zobacz [narzędzie XML Serializer Generator (Sgen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowane**

Kliknij, aby wyświetlić okno dialogowe [Zaawansowane ustawienia kompilacji (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okna dialogowego.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)