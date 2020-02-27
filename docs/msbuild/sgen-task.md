---
title: SGen — zadanie | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4305f27435d97c346ce623a21b37f011fd8da0cd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632306"
---
# <a name="sgen-task"></a>SGen — Zadanie

Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie otacza narzędzie generatora serializatora XML (*Sgen. exe*). Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatorów XML (Sgen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `SGen`.

| Parametr | Opis |
|-----------------------------| - |
| `BuildAssemblyName` | Wymagany `String` parametr.<br /><br /> Zestaw, dla którego ma zostać wygenerowany kod serializacji. |
| `BuildAssemblyPath` | Wymagany `String` parametr.<br /><br /> Ścieżka do zestawu, dla którego ma zostać wygenerowany kod serializacji. |
| `DelaySign` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz użyć w pełni podpisanego zestawu.<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest używany z parametrem `KeyFile` lub `KeyContainer`. |
| `KeyContainer` | Opcjonalny parametr `String`.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to podpisywanie zestawu przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. |
| `KeyFile` | Opcjonalny parametr `String`.<br /><br /> Określa parę kluczy lub klucz publiczny do użycia w celu podpisania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Pobiera lub ustawia platformę kompilatora używaną do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86`, `x64`lub `anycpu`. Wartość domyślna to `anycpu`. |
| `References` | Opcjonalny parametr `String[]`.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML. |
| `SdkToolsPath` | Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *Resgen. exe*. |
| `SerializationAssembly` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera wygenerowany zestaw serializacji. |
| `SerializationAssemblyName` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę wygenerowanego zestawu serializacji. |
| `ShouldGenerateSerializer` | Wymagany `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie SGen powinno generować zestaw serializacji. |
| `Timeout` | Opcjonalny parametr `Int32`.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `ToolPath` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (*Sgen. exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, w której działa program MSBuild. |
| `Types` | Opcjonalny parametr `String[]`.<br /><br /> Pobiera lub ustawia listę konkretnych typów, dla których ma zostać wygenerowany kod serializacji. SGen generuje kod serializacji tylko dla tych typów. |
| `UseProxyTypes` | Wymagany `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie SGen generuje kod serializacji tylko dla typów serwera proxy usługi sieci Web XML. |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
