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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c326dc31f6ce80026f1c83c5b71f8e27faabf93e
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887631"
---
# <a name="sgen-task"></a>SGen — Zadanie
Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie otacza narzędzie generatora serializatora XML (*Sgen. exe*). Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatorów XML (Sgen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `SGen` zadania.

| Parametr | Opis |
|-----------------------------| - |
| `BuildAssemblyName` | Wymagany `String` parametr.<br /><br /> Zestaw, dla którego ma zostać wygenerowany kod serializacji. |
| `BuildAssemblyPath` | Wymagany `String` parametr.<br /><br /> Ścieżka do zestawu, dla którego ma zostać wygenerowany kod serializacji. |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz użyć w pełni podpisanego zestawu.<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest `KeyFile` używany `KeyContainer` z parametrem or. |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to podpisywanie zestawu przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa parę kluczy lub klucz publiczny do użycia w celu podpisania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia platformę kompilatora używaną do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. |
| `References` | Opcjonalny `String[]` parametr.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML. |
| `SdkToolsPath` | Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *Resgen. exe*. |
| `SerializationAssembly` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr wyjściowy.<br /><br /> Zawiera wygenerowany zestaw serializacji. |
| `SerializationAssemblyName` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę wygenerowanego zestawu serializacji. |
| `ShouldGenerateSerializer` | Wymagany `Boolean` parametr.<br /><br /> Jeśli `true`zadanie Sgen powinno generować zestaw serializacji. |
| `Timeout` | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `ToolPath` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (*Sgen. exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Types` | Opcjonalny `String[]` parametr.<br /><br /> Pobiera lub ustawia listę konkretnych typów, dla których ma zostać wygenerowany kod serializacji. SGen generuje kod serializacji tylko dla tych typów. |
| `UseProxyTypes` | Wymagany `Boolean` parametr.<br /><br /> Jeśli `true`zadanie SGen generuje kod serializacji tylko dla typów serwera proxy usługi sieci Web XML. |

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> z klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)