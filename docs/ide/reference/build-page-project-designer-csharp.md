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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf50c653d82a7de22d5a81fd81c38db0db1be8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76923268"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)

Użyj **strony Kompilacja** **projektanta projektu,** aby określić właściwości konfiguracji kompilacji projektu. Ta strona dotyczy [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tylko projektów.

Aby uzyskać dostęp do strony **Kompilacja,** wybierz węzeł projektu (a nie węzeł **Rozwiązanie)** w **Eksploratorze rozwiązań**. Następnie wybierz polecenie **Wyświetl**strony **właściwości** w menu. Po wyświetleniu projektanta projektu wybierz kartę **Kompilacja.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Poniższe opcje umożliwiają wybranie konfiguracji i platformy do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W uproszczonych konfiguracjach kompilacji system projektu określa, czy chcesz utworzyć wersję debugowania lub wersji. W związku z tym te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie konfiguracji debugowania i zwalniania](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfiguracja**

Określa ustawienia konfiguracji, które mają być wyświetlane lub modyfikowane. Ustawienia mogą być **aktywne (debugowanie)** (jest to ustawienie domyślne), **Debugowanie,** **Zwalnianie**lub **Wszystkie konfiguracje**.

**Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Domyślnym ustawieniem jest **Active (Dowolny procesor)**. Aktywną platformę można zmienić za pomocą **programu Menedżer konfiguracji**. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.

**Symbole kompilacji warunkowej**

Określa symbole, na których ma być wykonywane kompilacje warunkowe. Oddziel symbole średnikiem (";"). Aby uzyskać więcej informacji, zobacz [/define (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Zdefiniuj stałą DEBUG**

Definiuje DEBUG jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tej opcji jest `/define:DEBUG` równoznaczne z użyciem opcji wiersza polecenia.

**Zdefiniuj stałą TRACE**

Definiuje TRACE jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tej opcji jest `/define:TRACE` równoznaczne z użyciem opcji wiersza polecenia.

**Docelowy obiekt platformy**

Określa procesor, na który ma docelow plik wyjściowy. Wybierz **x86** dla dowolnego 32-bitowego procesora zgodnego z procesorem Intel, wybierz **x64** dla dowolnego 64-bitowego procesora zgodnego z procesorem Intel, wybierz **arm** dla procesorów ARM lub wybierz **dowolny procesor,** aby określić, że dowolny procesor jest dopuszczalny. **Każdy procesor CPU** jest wartością domyślną dla projektów, ponieważ umożliwia aplikacji do uruchamiania na najszerszym zakresie sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Dopuszczający wartość null**

Określa kontekst c# null do realizacji w całym projekcie. Ta opcja interfejsu użytkownika została wprowadzona w programie Visual Studio 16.5 i jest włączona tylko dla projektów, które używają języka C# 8.0 lub nowszego.

Aby uzyskać więcej informacji, zobacz [Konteksty nullable](/dotnet/csharp/nullable-references#nullable-contexts).

**Preferuj 32-bitowe**

Jeśli zaznaczone jest pole wyboru **Preferuj32-bitowe,** aplikacja działa jako aplikacja 32-bitowa zarówno w 32-bitowych, jak i 64-bitowych wersjach systemu Windows. Jeśli to pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w 64-bitowych wersjach systemu Windows.

Jeśli uruchomisz aplikację jako aplikację 64-bitową, rozmiar wskaźnika podwaja się, a problemy ze zgodnością mogą wystąpić z innymi bibliotekami, które są wyłącznie 32-bitowe. Jest to przydatne do uruchamiania aplikacji 64-bitowej tylko wtedy, gdy potrzebuje więcej niż 4 GB pamięci lub instrukcje 64-bitowe zapewniają znaczną poprawę wydajności.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie Kompilacja**lista **docelowa platformy** jest ustawiona na **dowolny procesor.**

- Na **stronie aplikacji**lista **Typ wyjściowy** określa, że projekt jest aplikacją.

- Na **stronie aplikacji**lista **docelowa framework** określa .NET Framework 4.5.

**Zezwalaj na niebezpieczny kod**

Umożliwia kod, który używa [niebezpiecznego](/dotnet/csharp/language-reference/keywords/unsafe) słowa kluczowego do kompilacji. Aby uzyskać więcej informacji, zobacz [/unsafe (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optymalizacja kodu**

Włącz lub wyłącz optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i wydajniejszy. Aby uzyskać więcej informacji, zobacz [/optimize (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

Następujące ustawienia są używane do konfigurowania opcji błędu i ostrzeżenia dla procesu kompilacji.

**Poziom ostrzeżenia**

Określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/warn (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Pomijanie ostrzeżeń**

Blokuje możliwość generowania przez kompilator jednego lub więcej ostrzeżeń. Oddziel wiele numerów ostrzegawczych przecinkiem lub średnikiem. Aby uzyskać więcej informacji, zobacz [/nowarn (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Potraktuj ostrzeżenia jako błędy

Następujące ustawienia są używane do określenia, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z następujących opcji, aby wskazać, w jakich warunkach ma zwrócić błąd, gdy kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Brak** — nie traktuje żadnych ostrzeżeń jako błędów.

**Wszystkie** — traktuje wszystkie ostrzeżenia jako błędy.

**Określone ostrzeżenia** — traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzegawczych przecinkiem lub średnikiem.

> [!TIP]
> Jeśli nie chcesz, aby ostrzeżenia dotyczące analizy kodu były traktowane jako błędy, zobacz Często zadawane pytania [dotyczące analizy kodu.](../../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="output"></a>Dane wyjściowe

Następujące ustawienia są używane do konfigurowania opcji wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa**

Określa lokalizację plików wyjściowych dla konfiguracji tego projektu. Wprowadź ścieżkę danych wyjściowych kompilacji w tym polu lub wybierz przycisk **Przeglądaj,** aby określić ścieżkę. Ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie on zapisany jako względny. Domyślną ścieżką jest bin\Debug\\lub bin\Release .

W uproszczonych konfiguracjach kompilacji system projektu określa, czy chcesz utworzyć wersję debugowania lub wersji. Polecenie **Kompilacja** z menu **Debugowanie** (F5) umieści kompilację w lokalizacji debugowania, niezależnie od określonej **ścieżki wyjściowej.** Jednak **build** polecenia z **build** menu umieszcza go w lokalizacji, którą określisz. Aby uzyskać więcej informacji, zobacz [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

**Plik dokumentacji XML**

Określa nazwę pliku, do którego będą przetwarzane komentarze do dokumentacji. Aby uzyskać więcej informacji, zobacz [/doc (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Zarejestruj się w com interop**

Wskazuje, że aplikacja zarządzana będzie uwidacznia obiekt COM (otoka wywoływana przez COM), która umożliwia obiektowi COM interakcję z aplikacją zarządzaną. Właściwość **typ danych wyjściowych** na [stronie Aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) **projektanta projektu** dla tej aplikacji musi być ustawiona na **Biblioteka klas,** aby właściwość **Register for COM interop** była dostępna. Przykładowa klasa, którą można [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] uwzględnić w aplikacji i udostępnić jako obiekt COM, zobacz [przykładową klasę COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generowanie złożenia serializacji**

Określa, czy kompilator będzie używał narzędzia Generatora serializatora XML (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji można poprawić wydajność <xref:System.Xml.Serialization.XmlSerializer> uruchamiania, jeśli użyto tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest **ustawiona**na Auto , który określa, że <xref:System.Xml.Serialization.XmlSerializer> zestawy serializacji są generowane tylko wtedy, gdy użyto do kodowania typów w kodzie do XML. **Off** określa, że zestawy serializacji nigdy nie są generowane, <xref:System.Xml.Serialization.XmlSerializer>niezależnie od tego, czy używany jest kod. **Na** określa, że zestawy serializacji zawsze być generowane. Zestawy serializacji mają `TypeName`nazwy . XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [Narzędzie generatora serializatora XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowane**

Kliknij, aby wyświetlić [okno dialogowe Okno dialogowe Zaawansowane ustawienia kompilacji (C#).](../../ide/reference/advanced-build-settings-dialog-box-csharp.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora języka C#](/dotnet/csharp/language-reference/compiler-options/index)
