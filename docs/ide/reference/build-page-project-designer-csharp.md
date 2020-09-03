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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7da7414b9cf454e861c8407633de7851dcb86df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419227"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)

Użyj strony **kompilacja** **projektanta projektu** , aby określić właściwości konfiguracji kompilacji projektu. Ta strona ma zastosowanie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tylko do projektów.

Aby uzyskać dostęp do strony **kompilacja** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **Widok**, **strony właściwości** w menu. Gdy zostanie wyświetlony Projektant projektu, wybierz kartę **kompilacja** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. W związku z tym te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [How to: Set Debug and Release Configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **aktywne (Debugowanie)** (jest to ustawienie domyślne), **debugowanie**, **wydanie**lub **wszystkie konfiguracje**.

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienie domyślne jest **aktywne (dowolny procesor)**. Możesz zmienić aktywną platformę przy użyciu **Configuration Manager**. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.

**Symbole kompilacji warunkowej**

Określa symbole, na których ma zostać wykonana Kompilacja warunkowa. Oddzielaj symbole średnikami (";"). Aby uzyskać więcej informacji, zobacz [/define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Zdefiniuj stałą DEBUG**

Definiuje debugowanie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoważne użyciu `/define:DEBUG` opcji wiersza polecenia.

**Zdefiniuj stałą TRACE**

Definiuje śledzenie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoważne użyciu `/define:TRACE` opcji wiersza polecenia.

**Obiekt docelowy platformy**

Określa procesor, który ma być przeznaczony dla pliku wyjściowego. Wybierz opcję **x86** dla dowolnego 32-bitowego procesora zgodnego z technologią Intel, wybierz **x64** dla dowolnego 64-bitowego procesora zgodnego z technologią Intel, wybierz pozycję **ARM** dla procesorów ARM lub wybierz **dowolny** procesor, aby określić, że każdy z procesorów jest akceptowalny. **Każdy procesor** jest wartością domyślną dla projektów, ponieważ umożliwia uruchamianie aplikacji na najszerszym zakresie sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Wymaga**

Określa kontekst wartości null dla całego projektu. Ta opcja interfejsu użytkownika została wprowadzona w programie Visual Studio 16,5 i jest włączona tylko dla projektów korzystających z języka C# 8,0 lub nowszego.

Aby uzyskać więcej informacji, zobacz [konteksty dopuszczające wartości null](/dotnet/csharp/nullable-references#nullable-contexts).

**Preferuj 32-bitowe**

Jeśli pole wyboru **Prefer32-bitowy** jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa na 32-bitowej i 64-bitowej wersji systemu Windows. Jeśli to pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bit w systemie 64-bitowe wersje systemu Windows.

Jeśli aplikacja jest uruchamiana jako aplikacja 64-bitowa, rozmiar wskaźnika podwaja się i problemy ze zgodnością mogą wystąpić w przypadku innych bibliotek, które są wyłącznie 32-bitowe. Warto uruchamiać aplikacje 64-bitowe tylko wtedy, gdy potrzebują więcej niż 4 GB pamięci lub instrukcje 64-bitowe zapewniają znaczący wzrost wydajności.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie kompilacja**na liście **docelowy platformy** jest ustawiona wartość **dowolny procesor CPU**.

- Na **stronie aplikacja**na liście **typ wyjścia** określa, że projekt jest aplikacją.

- Na **stronie aplikacja**lista **platform docelowych** określa .NET Framework 4,5.

**Zezwalaj na niebezpieczny kod**

Zezwala na kompilowanie kodu, który używa [niebezpiecznego](/dotnet/csharp/language-reference/keywords/unsafe) słowa kluczowego. Aby uzyskać więcej informacji, zobacz [/unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optymalizuj kod**

Włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny. Aby uzyskać więcej informacji, zobacz [/Optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Poniższe ustawienia służą do konfigurowania opcji błędu i ostrzeżenia dla procesu kompilacji.

**Poziom ostrzeżeń**

Określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Pomijanie ostrzeżeń**

Blokuje możliwość generowania co najmniej jednego ostrzeżenia przez kompilator. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Poniższe ustawienia służą do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z następujących opcji, aby wskazać, w których warunkach ma zostać zwrócony błąd, gdy kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Brak** — nie traktuje żadnych ostrzeżeń jako błędów.

**Wszystkie** — traktuje wszystkie ostrzeżenia jako błędy.

**Określone ostrzeżenia** — traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.

> [!TIP]
> Jeśli nie chcesz, aby ostrzeżenia analizy kodu były traktowane jak błędy, zobacz [często zadawane pytania dotyczące analizy kodu](../../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="output"></a>Dane wyjściowe

Poniższe ustawienia służą do konfigurowania opcji danych wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa**

Określa lokalizację plików wyjściowych dla konfiguracji projektu. Wprowadź ścieżkę do danych wyjściowych kompilacji w tym polu lub wybierz przycisk **Przeglądaj** , aby określić ścieżkę. Ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie ona zapisana jako względna. Ścieżka domyślna to bin\Debug lub bin\Release \\ .

W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. Polecenie **Build** z menu **Debuguj** (F5) umieści kompilację w lokalizacji debugowania niezależnie od określonej **ścieżki wyjściowej** . Jednak polecenie **Build** z menu **kompilacja** umieszcza je w określonej lokalizacji. Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

**Plik dokumentacji XML**

Określa nazwę pliku, do którego zostaną przetworzone komentarze dokumentacji. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Rejestracja w celu współdziałania z modelem COM**

Wskazuje, że aplikacja zarządzana uwidacznia obiekt COM (otoka COM, która jest wywoływana), która umożliwia obiektowi COM współpracujące z zarządzaną aplikacją. Właściwość **Typ danych wyjściowych** na [stronie aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) **projektanta projektu** dla tej aplikacji musi być ustawiona na wartość **Biblioteka klas** , aby właściwość **register dla elementu com** była dostępna. Aby zapoznać się z przykładową klasą, którą można uwzględnić w [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] aplikacji i uwidocznić jako obiekt com, zobacz [przykład klasy com](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generuj zestaw serializacji**

Określa, czy kompilator będzie używać narzędzie XML Serializer Generator (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania, <xref:System.Xml.Serialization.XmlSerializer> Jeśli użyto tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na wartość **automatycznie**, co oznacza, że zestawy serializacji są generowane tylko wtedy, gdy używane jest <xref:System.Xml.Serialization.XmlSerializer> kodowanie typów w kodzie do formatu XML. **Wyłączone** określa, że zestawy serializacji nigdy nie są generowane, bez względu na to, czy kod używa <xref:System.Xml.Serialization.XmlSerializer> . **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji mają nazwę `TypeName`.XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [narzędzie XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowany**

Kliknij, aby wyświetlić okno dialogowe [Zaawansowane ustawienia kompilacji (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okno dialogowe.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)
