---
title: Zadanie SGen | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632306"
---
# <a name="sgen-task"></a>SGen — Zadanie

Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie zawija narzędzie Generator serializatora XML *(Sgen.exe).* Aby uzyskać więcej informacji, zobacz [narzędzie XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry

 W poniższej tabeli `SGen` opisano parametry zadania.

| Parametr | Opis |
|-----------------------------| - |
| `BuildAssemblyName` | Wymagany parametr interfejsu `String`.<br /><br /> Zestaw do generowania kodu serializacji dla. |
| `BuildAssemblyPath` | Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka do zestawu do generowania kodu serializacji dla. |
| `DelaySign` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa, że chcesz umieścić tylko klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz w pełni podpisany zestaw.<br /><br /> Ten parametr nie ma wpływu, `KeyFile` chyba `KeyContainer` że jest używany z lub parametru. |
| `KeyContainer` | Parametr `String` opcjonalny.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to podpisanie zestawu przez wstawienie klucza publicznego do manifestu zestawu. Zadanie podpisze zestaw końcowy za pomocą klucza prywatnego. |
| `KeyFile` | Parametr `String` opcjonalny.<br /><br /> Określa parę kluczy lub klucz publiczny, który ma być używany do podpisywania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Pobiera lub ustawia platformę kompilatora używane do generowania zestawu wyjściowego. Ten parametr może mieć `x86` `x64`wartość `anycpu`, lub . Wartość domyślna to `anycpu`. |
| `References` | Parametr `String[]` opcjonalny.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML. |
| `SdkToolsPath` | Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*. |
| `SerializationAssembly` | Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera wygenerowany zestaw serializacji. |
| `SerializationAssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę wygenerowanego zestawu serializacji. |
| `ShouldGenerateSerializer` | Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true`zadanie SGen należy wygenerować zestaw serializacji. |
| `Timeout` | Parametr `Int32` opcjonalny.<br /><br /> Określa czas w milisekundach, po upływie którego plik wykonywalny zadania zostanie zakończony. Wartością domyślną jest `Int.MaxValue`, wskazując, że nie ma okresu przeoczynia. |
| `ToolPath` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowane bazowym plikiem wykonywalnym (*sgen.exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji SDK odpowiadającej wersji struktury z uruchomionym msbuild. |
| `Types` | Parametr `String[]` opcjonalny.<br /><br /> Pobiera lub ustawia listę określonych typów do generowania kodu serializacji dla. SGen wygeneruje kod serializacji tylko dla tych typów. |
| `UseProxyTypes` | Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true`zadanie SGen generuje kod serializacji tylko dla typów serwerów proxy usługi sieci Web XML. |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
