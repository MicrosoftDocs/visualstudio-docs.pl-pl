---
title: Strona kompilacji, Projektant projektu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21b572e99d23c882f90a1e9218e7a52fb94aedb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660908"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj strony **kompilacja** **projektanta projektu** , aby określić właściwości konfiguracji kompilacji projektu. Ta strona ma zastosowanie [!INCLUDE[csprcs](../../includes/csprcs-md.md)] tylko do projektów.

 Aby uzyskać dostęp do strony **kompilacja** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **kompilacja** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma
 Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

> [!NOTE]
> W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. W związku z tym te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Konfiguracja** Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia mogą być **aktywne (Debugowanie)** (jest to ustawienie domyślne), **debugowanie**, **wydanie**lub **wszystkie konfiguracje**.

 **Platforma** Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienie domyślne jest **aktywne (dowolny procesor)**. Możesz zmienić aktywną platformę przy użyciu **Configuration Manager**. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne
 Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.

 **Symbole kompilacji warunkowej** Określa symbole, na których ma zostać wykonana Kompilacja warunkowa. Oddzielaj symbole średnikami (";"). Aby uzyskać więcej informacji, zobacz [/define (opcje kompilatora C#)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).

 **Zdefiniuj stałą DEBUG** Definiuje debugowanie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoznaczne z użyciem `/define:DEBUG` opcji wiersza polecenia.

 **Zdefiniuj stałą Trace** Definiuje śledzenie jako symbol we wszystkich plikach kodu źródłowego w aplikacji. Wybranie tego jest równoznaczne z użyciem `/define:TRACE` opcji wiersza polecenia.

 **Docelowy procesor CPU** Określa procesor, który ma być przeznaczony dla pliku wyjściowego. Wybierz opcję **x86** dla dowolnego 32-bitowego procesora zgodnego z technologią Intel, wybierz **x64** dla dowolnego 64-bitowego procesora zgodnego z technologią Intel, wybierz pozycję **ARM** dla procesorów ARM lub wybierz **dowolny** procesor, aby określić, że każdy z procesorów jest akceptowalny. **Każdy procesor** jest wartością domyślną dla projektów, ponieważ umożliwia uruchamianie aplikacji na najszerszym zakresie sprzętu.

 Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).

 **Preferuj 32-bitowe** Jeśli pole wyboru **Prefer32-bitowy** jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa na 32-bitowej i 64-bitowej wersji systemu Windows. Jeśli to pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bit w systemie 64-bitowe wersje systemu Windows.

 Jeśli aplikacja jest uruchamiana jako aplikacja 64-bitowa, rozmiar wskaźnika podwaja się i problemy ze zgodnością mogą wystąpić w przypadku innych bibliotek, które są wyłącznie 32-bitowe. Warto uruchamiać aplikacje 64-bitowe tylko wtedy, gdy potrzebują więcej niż 4 GB pamięci lub instrukcje 64-bitowe zapewniają znaczący wzrost wydajności.

 To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:

- Na **stronie kompilacja**na liście **docelowy platformy** jest ustawiona wartość **dowolny procesor CPU**.

- Na **stronie aplikacja**na liście **typ wyjścia** określa, że projekt jest aplikacją.

- Na **stronie aplikacja**lista **platform docelowych** określa .NET Framework 4,5.

  **Zezwalaj na niebezpieczny kod** Zezwala na kompilowanie kodu, który używa [niebezpiecznego](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) słowa kluczowego. Aby uzyskać więcej informacji, zobacz [/unsafe (opcje kompilatora C#)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).

  **Optymalizuj kod** Włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny. Aby uzyskać więcej informacji, zobacz [/Optimize (opcje kompilatora C#)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia
 Poniższe ustawienia służą do konfigurowania opcji błędu i ostrzeżenia dla procesu kompilacji.

 **Poziom ostrzeżeń** Określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/warn (opcje kompilatora C#)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).

 **Pomiń ostrzeżenia** Blokuje możliwość generowania co najmniej jednego ostrzeżenia przez kompilator. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy
 Poniższe ustawienia służą do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z następujących opcji, aby wskazać, w których warunkach ma zostać zwrócony błąd, gdy kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).

 **Brak** Nie traktuje żadnych ostrzeżeń jako błędów.

 **Określone ostrzeżenia** Traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.

 **Wszystkie** Traktuje wszystkie ostrzeżenia jako błędy.

## <a name="output"></a>Dane wyjściowe
 Poniższe ustawienia służą do konfigurowania opcji danych wyjściowych dla procesu kompilacji.

 **Ścieżka wyjściowa** Określa lokalizację plików wyjściowych dla konfiguracji projektu. Wprowadź ścieżkę do danych wyjściowych kompilacji w tym polu lub wybierz przycisk **Przeglądaj** , aby określić ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzisz ścieżkę bezwzględną, zostanie ona zapisana jako względna. Ścieżka domyślna to bin\Debug lub bin\Release \\ . Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 W przypadku uproszczonych konfiguracji kompilacji system projektu określa, czy należy utworzyć wersję Debug lub Release. Polecenie **Build** z menu **Debuguj** (F5) umieści kompilację w lokalizacji debugowania niezależnie od określonej **ścieżki wyjściowej** . Jednak polecenie **Build** z menu **kompilacja** umieszcza je w określonej lokalizacji. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Plik dokumentacji XML** Określa nazwę pliku, do którego zostaną przetworzone komentarze dokumentacji. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).

 **Rejestracja w celu** współdziałania z modelem com Wskazuje, że aplikacja zarządzana uwidacznia obiekt COM (otoka COM, która jest wywoływana), która umożliwia obiektowi COM współpracujące z zarządzaną aplikacją. Właściwość **Typ danych wyjściowych** na [stronie aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) **projektanta projektu** dla tej aplikacji musi być ustawiona na wartość **Biblioteka klas** , aby właściwość **register dla elementu com** była dostępna. Aby zapoznać się z przykładową klasą, którą można uwzględnić w [!INCLUDE[csprcs](../../includes/csprcs-md.md)] aplikacji i uwidocznić jako obiekt com, zobacz [przykład klasy com](https://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).

 **Generuj zestaw serializacji** Określa, czy kompilator będzie używać narzędzie XML Serializer Generator (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania, <xref:System.Xml.Serialization.XmlSerializer> Jeśli użyto tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na wartość **automatycznie**, co oznacza, że zestawy serializacji są generowane tylko wtedy, gdy używane jest <xref:System.Xml.Serialization.XmlSerializer> kodowanie typów w kodzie do formatu XML. **Wyłączone** określa, że zestawy serializacji nigdy nie są generowane, bez względu na to, czy kod używa <xref:System.Xml.Serialization.XmlSerializer> . **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji mają nazwę `TypeName`.XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [narzędzie XML Serializer Generator (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).

 **Zaawansowane** Kliknij, aby wyświetlić okno dialogowe [Zaawansowane ustawienia kompilacji (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okno dialogowe.

## <a name="see-also"></a>Zobacz też
 [Właściwości projektu odwołania](../../ide/reference/project-properties-reference.md) do [opcji kompilatora C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
