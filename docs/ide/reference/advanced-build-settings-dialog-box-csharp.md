---
title: Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 83dc69bb3856a7fe98e35cf66b0a6325c97a0651
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930153"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe

Użyj **Zaawansowane ustawienia kompilacji** okna dialogowego **projektanta projektu** określić najbardziej zaawansowane właściwości konfiguracji kompilacji projektu. Dotyczy to okno dialogowe [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] wyłącznie dla projektów.

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień zaawansowanych.

**Wersja językowa**

Określa wersję języka. Zestaw funkcji różni się w każdej wersji, ta opcja może służyć do wymusić na kompilatorze, aby zezwolić tylko podzbiór funkcji zaimplementowano lub włączyć tylko te funkcje, które są zgodne ze standardem istniejących. To ustawienie ma następujące opcje:

- **default**

   Jest przeznaczony dla bieżącej wersji.

- **ISO-1** i **ISO-2**

   Jest przeznaczony dla funkcji standard ISO-1 i ISO 2 odpowiednio.

- **C#[numer wersji]**

   Jest przeznaczony dla określonej wersji C#. Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).

**Wewnętrznych kompilatora raportowanie błędów**

Określa, czy należy zgłaszać błędy kompilatora do firmy Microsoft. Jeśli ustawiono **wiersza** (ustawienie domyślne), jeśli zostanie wyświetlony monit o wystąpi błąd wewnętrzny kompilatora, co daje możliwość elektronicznie wysłaniem raportu o błędach do firmy Microsoft. Jeśli ustawiono **wysyłania**, raport o błędzie zostanie automatycznie wysłane. Jeśli ustawiono **kolejki**, raporty o błędach zostanie umieszczona w kolejce. Jeśli ustawiono **Brak**, błąd jest zgłaszany tylko na kompilatora tekst wyjściowy. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Sprawdzaj przepełnienie/niedopełnienie arytmetyczne**

Określa, czy liczba całkowita arytmetyczne instrukcja, nie jest w zakresie [zaznaczone](/dotnet/csharp/language-reference/keywords/checked) lub [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) słów kluczowych i że wyniki w wartość spoza zakresu typu danych spowoduje, że środowiska wykonawczego wyjątek. Aby uzyskać więcej informacji, zobacz [/ checked (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Nie odwołuj się do biblioteki mscorlib.dll**

Określa, czy biblioteka mscorlib.dll zostaną zaimportowane do programu, definiując całą <xref:System> przestrzeni nazw. Zaznacz to pole wyboru, jeśli chcesz zdefiniować lub utworzyć własne <xref:System> przestrzeni nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Dane wyjściowe

Poniższe opcje umożliwiają określenie opcji zaawansowanych danych wyjściowych.

**Informacje o debugowaniu**

Określa typ informacji o debugowaniu generowanych przez kompilator. Aby uzyskać informacje dotyczące sposobu konfigurowania wydajność debugowania aplikacji, zobacz [ułatwianie obrazu do debugowania](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). To ustawienie ma następujące opcje:

- **Brak**

   Określa, zostanie wygenerowany nie informacji debugowania.

- **full**

   Umożliwia dołączanie debugera do uruchomionego programu.

- **"pdbonly"**

   Umożliwia kodu źródłowego, debugowanie, gdy program jest uruchomiony w debugerze, ale będą wyświetlane tylko asemblera, gdy uruchomiony program jest dołączony do debugera.

-  **Przenośna**

   Tworzy. Plik PDB, plik symboli nie określonej platformy, przenośną, który zawiera inne narzędzia, szczególnie debugery, informacje o tym, co znajduje się w głównym pliku wykonywalnego i jak został utworzony. Zobacz [przenośnego pliku PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) Aby uzyskać więcej informacji.

- **Osadzony**

   Osadza informacje o symbolach przenośne w zestawie. Nie zewnętrznych. Generowany jest plik PDB.

Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Wyrównanie pliku**

Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**, i **8192**. Te wartości są mierzone w bajtach. Każda sekcja będzie wyrównany na granicy, która jest wielokrotnością liczby tę wartość, mających wpływ na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Adres podstawowy biblioteki**

Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [/baseAddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)