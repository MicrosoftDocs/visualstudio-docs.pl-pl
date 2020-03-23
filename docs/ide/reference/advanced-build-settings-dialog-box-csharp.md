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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f25f9d96cd8de8dcb140c79c7dfb3a7a5981986c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595855"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Okno dialogowe Zaawansowane ustawienia kompilacji (C#)

Okno dialogowe **Zaawansowane ustawienia kompilacji** **projektanta projektu** służy do określania właściwości zaawansowanej konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko projektów języka C#.

## <a name="general"></a>Ogólne

Poniższe opcje umożliwiają ustawienie ogólnych ustawień zaawansowanych.

**Wersja językowa**

::: moniker range=">=vs-2019"

Łącza do [/langversion (opcje kompilatora Języka C#),](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)który zawiera informacje o tym, jak domyślna wersja językowa jest wybierana na podstawie struktury docelowej projektu.

::: moniker-end

::: moniker range="vs-2017"

Określa wersję języka, którego chcesz użyć. Zestaw funkcji jest inny w każdej wersji, więc ta opcja może służyć do wymuszenia kompilatora, aby zezwolić tylko na podzbiór zaimplementowanych funkcji lub włączyć tylko te funkcje zgodne z istniejącym standardem.

Wartością domyślną jest C# 7.0.

::: moniker-end

**Raportowanie błędów kompilatora wewnętrznego**

Określa, czy mają być raportowane błędy kompilatora do firmy Microsoft. Jeśli ustawiono **monit** (domyślnie), zostanie wyświetlony monit o wystąpienie błędu kompilatora wewnętrznego, co daje możliwość wysłania raportu o błędzie drogą elektroniczną do firmy Microsoft. Jeśli ustawiona jest opcja **wyślij,** raport o błędzie zostanie wysłany automatycznie. Jeśli ustawiono **kolejkę,** raporty o błędach będą umieszczane w kolejce. Jeśli ustawiona na **brak,** błąd zostanie zgłoszony tylko w danych wyjściowych tekstu kompilatora. Aby uzyskać więcej informacji, zobacz [/errorreport (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Sprawdź, czy przepełnienie/niedopełnienie arytmetyczne**

Określa, czy instrukcja arytmetyczna liczba całkowita, która nie znajduje się w zakresie [sprawdzonych](/dotnet/csharp/language-reference/keywords/checked) lub [niesprawdzonych](/dotnet/csharp/language-reference/keywords/unchecked) słów kluczowych i która powoduje wartość poza zakresem typu danych spowoduje wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [/checked (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Nie odwoływać się do pliku mscorlib.dll**

Określa, czy mscorlib.dll zostanie zaimportowany do <xref:System> programu, definiując całą przestrzeń nazw. Zaznacz to pole wyboru, jeśli chcesz <xref:System> zdefiniować lub utworzyć własną przestrzeń nazw i obiekty. Aby uzyskać więcej informacji, zobacz [/nostdlib (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Dane wyjściowe

Poniższe opcje umożliwiają określenie zaawansowanych opcji wyjściowych.

**Informacje debugowania**

Określa typ informacji debugowania generowanych przez kompilator. Aby uzyskać informacje dotyczące konfigurowania wydajności debugowania aplikacji, zobacz [Ułatwianie debugowania obrazu.](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug) To ustawienie ma następujące opcje:

- **brak**

   Określa, że nie będą generowane żadne informacje debugowania.

- **Pełne**

   Umożliwia podłączenie debugera do uruchomionego programu.

- **pdbonly**

   Umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale będzie wyświetlany asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera.

- **Przenośne**

   Tworzy plik . Plik PDB, niespecyfowany na platformie, przenośny plik symboli, który zapewnia inne narzędzia, zwłaszcza debugery, informacje o tym, co znajduje się w głównym pliku wykonywalnym i jak został wyprodukowany. Aby uzyskać więcej informacji, zobacz [Przenośny plik PDB.](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)

- **Osadzone**

   Osadza przenośne informacje o symbolu w złożeniu. Brak zewnętrznego . Plik PDB jest produkowany.

Aby uzyskać więcej informacji, zobacz [/debug (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Wyrównanie pliku**

Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**i **8192**. Wartości te są mierzone w bajtach. Każda sekcja zostanie wyrównana do granicy, która jest wielokrotnością tej wartości, co wpływa na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealign (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Adres podstawowy biblioteki**

Określa preferowany adres podstawowy, pod którym ma być ładowana biblioteka DLL. Domyślny adres podstawowy biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego programu .NET Framework. Aby uzyskać więcej informacji, zobacz [/baseaddress (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
