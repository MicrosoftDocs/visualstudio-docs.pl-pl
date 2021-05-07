---
title: Strona kompilacji, Projektant projektu (C#)
description: Dowiedz się, jak używać strony Build (Kompilacja) projektanta projektu w Visual Studio, aby określić właściwości konfiguracji kompilacji projektu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 91b254f4c075693e23d8f650356cd97e86a4c746
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798560"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)

Użyj strony **Build** (Kompilacja) **projektanta projektu,** aby określić właściwości konfiguracji kompilacji projektu. Ta strona dotyczy tylko [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektów.

Aby uzyskać dostęp **do strony Kompilacja,** wybierz węzeł projektu (nie **węzeł** rozwiązania) w **Eksplorator rozwiązań**. Następnie wybierz **pozycję Wyświetl,** **strony właściwości** w menu. Gdy pojawi się projektant projektu, wybierz **kartę Kompilacja.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje umożliwiają wybranie konfiguracji i platformy do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję do debugowania, czy wydania. W związku z tym te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz How to: Set debug and release configurations ( Jak [ustawić konfiguracje debugowania i wydania).](../../debugger/how-to-set-debug-and-release-configurations.md)

**Konfiguracja**

Określa, które ustawienia konfiguracji mają być wyświetlane lub modyfikowane. Ustawieniami mogą być **Aktywne (debugowanie)** (ustawienie domyślne), **Debugowanie,** **Wydanie** lub **Wszystkie konfiguracje.**

**Platforma**

Określa, które ustawienia platformy mają być wyświetlane lub modyfikowane. Ustawieniem domyślnym jest **Aktywny (dowolny procesor CPU).** Aktywną platformę można zmienić przy użyciu **Menedżer konfiguracji**. Aby uzyskać więcej informacji, zobacz [Tworzyć i edytować konfiguracje.](../../ide/how-to-create-and-edit-configurations.md)

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.

**Symbole kompilacji warunkowej**

Określa symbole, na których należy wykonać kompilację warunkową. Oddziel symbole średnikiem (";"). Aby uzyskać więcej informacji, zobacz [/define (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)

**Definiowanie stałej DEBUG**

Definiuje DEBUG jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:DEBUG` opcji wiersza polecenia.

**Definiowanie stałej TRACE**

Definiuje trace jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:TRACE` opcji wiersza polecenia.

**Element docelowy platformy**

Określa procesor, który ma być docelowy przez plik wyjściowy. Wybierz **procesor x86** dla dowolnego 32-bitowego procesora zgodnego z technologią Intel, wybierz procesor **x64** dla dowolnego 64-bitowego procesora zgodnego z technologią Intel, wybierz pozycję **ARM** dla procesorów ARM lub wybierz pozycję Dowolny procesor **CPU,** aby określić, że dowolny procesor jest akceptowalny. **Każdy procesor** CPU jest wartością domyślną dla projektów, ponieważ umożliwia uruchamianie aplikacji na najszerszym zakresie sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)

**Nullable**

Określa kontekst dopuszczania wartości null dla całego projektu w języku C#. Ta opcja interfejsu użytkownika została wprowadzona w Visual Studio 16.5 i jest włączona tylko dla projektów, które używają języka C# 8.0 lub nowszego.

Aby uzyskać więcej informacji, zobacz [Nullable Contexts (Konteksty dopuszczane do wartości null).](/dotnet/csharp/nullable-references#nullable-contexts)

**Preferuj 32-bitowe**

Jeśli pole **wyboru Preferuj 32-bitowe** jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. Jeśli to pole wyboru zostanie wyczyszone, aplikacja będzie uruchamiana jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w 64-bitowych wersjach systemu Windows.

Jeśli uruchamiasz aplikację jako aplikację 64-bitową, rozmiar wskaźnika podwaja się, a problemy ze zgodnością mogą wystąpić w przypadku innych bibliotek, które są wyłącznie 32-bitowe. Aplikacja 64-bitowa jest przydatna tylko wtedy, gdy wymaga więcej niż 4 GB pamięci lub instrukcje 64-bitowe zapewniają znaczącą poprawę wydajności.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na stronie **kompilacji** lista **Docelowa platforma** jest ustawiona na **wartość Dowolny procesor CPU.**

- Na **stronie aplikacji** na liście **Typ danych wyjściowych** określa się, że projekt jest aplikacją.

- Na **stronie aplikacji** na liście **Docelowa framework** jest .NET Framework 4.5.

**Zezwalaj na niebezpieczny kod**

Zezwala na kompilowanie kodu, który używa [niebezpiecznego](/dotnet/csharp/language-reference/keywords/unsafe) słowa kluczowego . Aby uzyskać więcej informacji, zobacz [/unsafe (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)

**Optymalizowanie kodu**

Włącz lub wyłącz optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny. Aby uzyskać więcej informacji, zobacz [/optimize (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Następujące ustawienia służą do konfigurowania opcji błędów i ostrzeżeń dla procesu kompilacji.

**Poziom ostrzeżenia**

Określa poziom do wyświetlenia dla ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/warn (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)

**Pomijanie ostrzeżeń**

Blokuje możliwość generowania przez kompilator jednego lub większej liczby ostrzeżeń. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Następujące ustawienia służą do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z następujących opcji, aby wskazać, w jakich warunkach ma być zwracany błąd, gdy kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)

**Brak** — nie traktuje ostrzeżeń jako błędów.

**Wszystkie** — traktuje wszystkie ostrzeżenia jako błędy.

**Określone ostrzeżenia** — traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.

> [!TIP]
> Jeśli nie chcesz, aby ostrzeżenia analizy kodu były traktowane jako błędy, zobacz [Analiza kodu — często zadawane pytania.](/visualstudio/code-quality/analyzers-faq#treat-warnings-as-errors)

## <a name="output"></a>Dane wyjściowe

Następujące ustawienia służą do konfigurowania opcji danych wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa**

Określa lokalizację plików wyjściowych dla konfiguracji tego projektu. Wprowadź ścieżkę danych wyjściowych kompilacji w tym polu lub wybierz przycisk **Przeglądaj,** aby określić ścieżkę. Ścieżka jest względna; W przypadku wprowadzenia ścieżki bezwzględnej zostanie ona zapisana jako względna. Ścieżka domyślna to bin\Debug lub \\ bin\Release.

W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy kompilować wersję debugowania, czy wydania. Polecenie **Kompilacja** z menu **Debugowanie** (F5) umieści kompilację w lokalizacji debugowania niezależnie od **określisz ścieżki** wyjściowej. Jednak polecenie **Build (Kompilacja)** z menu **Build (Kompilacja)** umieszcza je w określisz lokalizacji. Aby uzyskać więcej informacji, zobacz [Understanding Build Configurations (Opis konfiguracji kompilacji).](../../ide/understanding-build-configurations.md)

**Plik dokumentacji XML**

Określa nazwę pliku, w którym będą przetwarzane komentarze dokumentacji. Aby uzyskać więcej informacji, zobacz [/doc (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)

**Rejestrowanie w celu międzyopietowego com**

Wskazuje, że aplikacja zarządzana będzie uwidaczniać obiekt COM (otokę wywoływną COM), który umożliwia obiektowi COM interakcję z aplikacją zarządzaną. Właściwość **Typ danych wyjściowych** na stronie Aplikacja projektanta projektu  dla tej aplikacji  musi być ustawiona na wartość Biblioteka klas, aby właściwość międzyopcyjna Rejestruj dla com była dostępna. [](../../ide/reference/application-page-project-designer-visual-basic.md)  Aby uzyskać przykładową klasę, która może zostać dołączyć do aplikacji i uwidocznić jako [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] obiekt COM, zobacz [Przykładowa klasa COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generowanie zestawu serializacji**

Określa, czy kompilator będzie używać narzędzie XML Serializer Generator (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji może poprawić wydajność uruchamiania, jeśli używasz tej klasy do <xref:System.Xml.Serialization.XmlSerializer> serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na automatyczne **,** który określa, że zestawy serializacji są generowane tylko wtedy, gdy zostały użyte do kodowania typów w <xref:System.Xml.Serialization.XmlSerializer> kodzie XML. **Off** określa, że zestawy serializacji nigdy nie są generowane, niezależnie od tego, czy kod używa <xref:System.Xml.Serialization.XmlSerializer> . **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji są nazywane `TypeName`.XmlSerializers.dll. Aby uzyskać więcej informacji, [zobacz narzędzie XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowany**

Kliknij, aby wyświetlić [okno dialogowe Zaawansowane ustawienia kompilacji (C#).](../../ide/reference/advanced-build-settings-dialog-box-csharp.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora języka C#](/dotnet/csharp/language-reference/compiler-options/index)
