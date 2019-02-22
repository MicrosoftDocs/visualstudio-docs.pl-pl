---
title: Resolvecomreference — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86155da1a14516992841aa5e19de2606eb09fbd8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639066"
---
# <a name="resolvecomreference-task"></a>Resolvecomreference — zadanie
Przyjmuje listę wpisz jeden lub więcej nazw bibliotek lub *.tlb* pliki i jest rozpoznawana jako tych bibliotek typów do lokalizacji na dysku.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `ResolveCOMReference` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DelaySign`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, umieszcza klucz publiczny w zestawie. Jeśli `false`, w pełni podpisuje zestaw.|
|`EnvironmentVariables`|Opcjonalnie `String[]` parametru.<br /><br /> Tablica par zmiennych środowiskowych, oddzielone znaku równości. Te zmienne są przekazywane do zduplikowanych *tlbimp.exe* i *aximp.exe* dodatkowo do lub selektywnie zastępują, blok regularnych środowiska...|
|`ExecuteAsTool`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uruchamia *tlbimp.exe* i *aximp.exe* z odpowiedniego obiektu docelowego framework-procesem do generowania zestawów niezbędne otoki. Ten parametr umożliwia wielowersyjności kodu.|
|`IncludeVersionInInteropName`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wersja biblioteki typów, które zostaną uwzględnione w nazwa otoki. Wartość domyślna to `false`.|
|`KeyContainer`|Opcjonalnie `String` parametru.<br /><br /> Określa kontener, który zawiera pary kluczy publiczny/prywatny.|
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Określa element, który zawiera pary kluczy publiczny/prywatny.|
|`NoClassMembers`|Opcjonalnie `Boolean`parametru.|
|`ResolvedAssemblyReferences`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa odwołania rozpoznanego zestawu.|
|`ResolvedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa w pełni kwalifikowaną pliki na dysku, które odnoszą się do fizycznej lokalizacji biblioteki typów, które były dostarczane jako dane wejściowe dla tego zadania.|
|`ResolvedModules`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.|
|`SdkToolsPath`|Opcjonalnie <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Jeśli `ExecuteAsTool` jest `true`, ten parametr musi być równa ścieżkę narzędzi zestawu SDK dla framework w wersji docelowej.|
|`StateFile`|Opcjonalnie `String` parametru.<br /><br /> Określa plik pamięci podręcznej składnika modelu COM w sygnatur czasowych. Jeśli nie występuje każdego uruchomienia spowoduje to ponowne wygenerowanie wszystkich otoki.|
|`TargetFrameworkVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa wersję platformy docelowej projektu.<br /><br /> Wartość domyślna to `String.Empty`. co oznacza, że jest nie filtrowania dla odwołania, w oparciu o platformę docelową.|
|`TargetProcessorArchitecture`|Opcjonalnie `String` parametru.<br /><br /> Określa preferowany cel architektury procesora. Przekazany do *tlbimp.exe*  /machine flagi po translacji.<br /><br /> Wartość parametru powinna być członkiem <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|
|`TypeLibFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa ścieżkę pliku biblioteki typów do odwołań COM. Elementy zawarte w tym parametrze mogą zawierać metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję [TypeLibFiles elementu metadanych](#typelibfiles-item-metadata) poniżej.|
|`TypeLibNames`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa nazwy biblioteki typów, aby rozwiązać. Elementy zawarte w tym parametrze musi zawierać niektóre metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję [TypeLibNames elementu metadanych](#typelibnames-item-metadata) poniżej.|
|`WrapperOutputDirectory`|Opcjonalnie `String` parametru.<br /><br /> Lokalizacja na dysku, w którym została umieszczona wygenerowanego zestawu międzyoperacyjnego. Jeśli metadane tego elementu nie jest określona, zadanie używa ścieżkę bezwzględną katalogu, w którym znajduje się w pliku projektu.|

## <a name="typelibnames-item-metadata"></a>Metadane elementu TypeLibNames
 W poniższej tabeli opisano dostępne metadane elementu dla elementów przekazany do `TypeLibNames` parametru.

|Metadane|Opis|
|--------------|-----------------|
|`GUID`|Wymagany element metadanych.<br /><br /> Identyfikator GUID dla biblioteki typów. Metadane tego elementu nie jest określona, zadanie kończy się niepowodzeniem.|
|`VersionMajor`|Wymagany element metadanych.<br /><br /> Wersja główna biblioteki typów. Metadane tego elementu nie jest określona, zadanie kończy się niepowodzeniem.|
|`VersionMinor`|Wymagany element metadanych.<br /><br /> Wersja pomocnicza biblioteki typów. Metadane tego elementu nie jest określona, zadanie kończy się niepowodzeniem.|
|`LocaleIdentifier`|Opcjonalny element metadanych.<br /><br /> Identyfikator ustawień regionalnych (lub identyfikatora LCID) dla biblioteki typów. Podany jako wartość 32-bitowych, która identyfikuje ludzi język preferowany przez użytkownika, region lub aplikacji. Jeśli ten element metadanych nie jest określona, zadanie używa domyślny identyfikator ustawień regionalnych "0".|
|`WrapperTool`|Opcjonalny element metadanych.<br /><br /> Określa narzędzie otoki, który jest używany do generowania otoki zestawu dla tego typu biblioteki. Jeśli ten element metadanych nie jest określona, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne są następujące opcje dostępności, bez uwzględniania wielkości liter typelibs:<br /><br /> -   `Primary`: To narzędzie otoki użyć już wygenerowany podstawowy zestaw międzyoperacyjny dla składnika COM. Korzystając z tego narzędzia otoki, nie należy określać katalog wyjściowy otoki ponieważ który spowoduje, że zadanie nie powiedzie się.<br />-   `TLBImp`: To narzędzie otoki wygenerować zestaw międzyoperacyjny dla składnika COM.<br />-   `AXImp`: To narzędzie otoki wygenerować zestaw międzyoperacyjny dla formantu ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadane elementu TypeLibFiles
 W poniższej tabeli opisano dostępne metadane elementu dla elementów przekazany do `TypeLibFiles` parametru.

|Metadane|Opis|
|--------------|-----------------|
|`WrapperTool`|Opcjonalny element metadanych.<br /><br /> Określa narzędzie otoki, który jest używany do generowania otoki zestawu dla tego typu biblioteki. Jeśli ten element metadanych nie jest określona, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne są następujące opcje dostępności, bez uwzględniania wielkości liter typelibs:<br /><br /> -   `Primary`: To narzędzie otoki użyć już wygenerowany podstawowy zestaw międzyoperacyjny dla składnika COM. Korzystając z tego narzędzia otoki, nie należy określać katalog wyjściowy otoki ponieważ który spowoduje, że zadanie nie powiedzie się.<br />-   `TLBImp`: To narzędzie otoki wygenerować zestaw międzyoperacyjny dla składnika COM.<br />-   `AXImp`: To narzędzie otoki wygenerować zestaw międzyoperacyjny dla formantu ActiveX.|

> [!NOTE]
>  Więcej informacji podasz do unikatowego identyfikowania bibliotekę typów, tym większa możliwość, że zadanie zostanie rozwiązany do prawidłowego pliku na dysku.

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [zadań klasy bazowej](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)