---
title: Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78817f65197c2dd295a6f2202f913c48b54e1ed9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748804"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Zaawansowane ustawienia kompilacji — okno dialogoweC#()

Za pomocą okna dialogowego **Zaawansowane ustawienia kompilacji** w **projektancie projektu** można określić zaawansowane właściwości konfiguracji kompilacji projektu. To okno dialogowe ma zastosowanie C# tylko do projektów.

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają ustawienie ogólnych ustawień zaawansowanych.

**Wersja językowa**

::: moniker range=">=vs-2019"

Linki do [/langversion (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), które zawierają informacje o tym, jak domyślna wersja językowa jest wybierana na podstawie platformy docelowej projektu.

::: moniker-end

::: moniker range="vs-2017"

Określa wersję języka do użycia. Zestaw funkcji różni się w każdej wersji, dlatego można użyć tej opcji, aby wymusić, aby kompilator zezwalał tylko na podzbiór wdrożonych funkcji, lub aby włączyć tylko te funkcje, które są zgodne z istniejącym standardem.

Wartość domyślna to C# 7,0.

::: moniker-end

**Raportowanie wewnętrznego błędu kompilatora**

Określa, czy raportować błędy kompilatora do firmy Microsoft. Jeśli zostanie ustawiony **monit** (domyślnie), zostanie wyświetlony monit o podanie, czy wystąpił wewnętrzny błąd kompilatora, co umożliwia wysłanie raportu o błędach do firmy Microsoft. W przypadku wybrania opcji **Wyślij**raport o błędach zostanie wysłany automatycznie. W przypadku ustawienia wartości **Queue**raporty o błędach będą umieszczane w kolejce. W przypadku wybrania wartości **none**błąd będzie raportowany tylko w danych wyjściowych kompilatora. Aby uzyskać więcej informacji, zobacz [/errorreportC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Sprawdź, czy jest przepełnienie arytmetyczne/nadmiarowy**

Określa, czy instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w zakresie [zaznaczonych](/dotnet/csharp/language-reference/keywords/checked) lub [niesprawdzonych](/dotnet/csharp/language-reference/keywords/unchecked) słów kluczowych i powoduje, że wartość spoza zakresu typu danych spowoduje wystąpienie wyjątku czasu wykonywania. Aby uzyskać więcej informacji, zobacz [/CheckedC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Nie Odwołuj się do biblioteki mscorlib. dll**

Określa, czy biblioteka mscorlib. dll zostanie zaimportowana do programu w celu zdefiniowania całej przestrzeni nazw <xref:System>. Zaznacz to pole wyboru, jeśli chcesz zdefiniować lub utworzyć własne <xref:System> przestrzeni nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlibC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Dane wyjściowe

Poniższe opcje pozwalają określić zaawansowane opcje wyjściowe.

**Informacje o debugowaniu**

Określa typ informacji o debugowaniu generowanych przez kompilator. Informacje o sposobie konfigurowania wydajności debugowania aplikacji znajdują się w temacie [ułatwianie debugowania obrazu](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). To ustawienie ma następujące opcje:

- **dawaj**

   Określa, że nie będą generowane żadne informacje o debugowaniu.

- **szczegółowe**

   Umożliwia dołączenie debugera do działającego programu.

- **pdbonly**

   Zezwala na Debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale tylko w przypadku, gdy uruchomiony program zostanie dołączony do debugera.

- **przenośne**

   Tworzy. Plik PDB, plik symboliczny niezależny od platformy, który udostępnia inne narzędzia, w szczególności debugery, informacje o tym, co znajduje się w głównym pliku wykonywalnym i sposobie jego wygenerowania. Aby uzyskać więcej informacji, zobacz [przenośny plik PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) .

- **osadzić**

   Osadza informacje o symbolu przenośnym w zestawie. Brak zewnętrznego. Plik PDB jest tworzony.

Aby uzyskać więcej informacji, zobacz [/DebugC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Wyrównanie pliku**

Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**i **8192**. Te wartości są mierzone w bajtach. Każda sekcja zostanie wyrównana na granicy, która jest wielokrotnością tej wartości, co wpływa na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealignC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Adres podstawowy biblioteki**

Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework. Aby uzyskać więcej informacji, zobacz [/BaseAddressC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora języka C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
