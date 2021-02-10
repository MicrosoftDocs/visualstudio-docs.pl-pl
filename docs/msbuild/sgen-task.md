---
title: SGen — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania SGen, aby utworzyć zestaw serializacji XML dla typów, przez otokę narzędzia generatora serializatora XML Sgen.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 476255e92326b7e9dae950512a5d27871ede2cc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937852"
---
# <a name="sgen-task"></a>SGen — Zadanie

Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie otacza narzędzie generatora serializatora XML (*Sgen.exe*). Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatorów XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `SGen` zadania.

| Parametr | Opis |
|-----------------------------| - |
| `BuildAssemblyName` | Wymagany parametr interfejsu `String`.<br /><br /> Zestaw, dla którego ma zostać wygenerowany kod serializacji. |
| `BuildAssemblyPath` | Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka do zestawu, dla którego ma zostać wygenerowany kod serializacji. |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false` , określa, że chcesz użyć w pełni podpisanego zestawu.<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest używany z `KeyFile` `KeyContainer` parametrem or. |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to podpisywanie zestawu przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa parę kluczy lub klucz publiczny do użycia w celu podpisania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia platformę kompilatora używaną do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86` , `x64` , lub `anycpu` . Wartość domyślna to `anycpu`. |
| `References` | Opcjonalny `String[]` parametr.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML. |
| `SdkToolsPath` | Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*. |
| `SerializationAssembly` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera wygenerowany zestaw serializacji. |
| `SerializationAssemblyName` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę wygenerowanego zestawu serializacji. |
| `ShouldGenerateSerializer` | Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true` zadanie Sgen powinno generować zestaw serializacji. |
| `Timeout` | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu. |
| `ToolPath` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (*sgen.exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, w której działa program MSBuild. |
| `Types` | Opcjonalny `String[]` parametr.<br /><br /> Pobiera lub ustawia listę konkretnych typów, dla których ma zostać wygenerowany kod serializacji. SGen generuje kod serializacji tylko dla tych typów. |
| `UseProxyTypes` | Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true` zadanie SGen generuje kod serializacji tylko dla typów serwera proxy usługi sieci Web XML. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
