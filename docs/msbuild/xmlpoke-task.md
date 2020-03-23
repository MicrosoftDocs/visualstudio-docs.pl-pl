---
title: XmlPoke zadanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588385"
---
# <a name="xmlpoke-task"></a>XmlPoke — zadanie

Ustawia wartości określone przez kwerendę XPath w pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `XmlPoke` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Parametr `String` opcjonalny.<br /><br /> Określa przestrzenie nazw prefiksów kwerend XPath. `Namespaces`jest fragmentem kodu XML `Namespace` składającym `Prefix` się `Uri`z elementów z atrybutami i . Atrybut `Prefix` określa prefiks do skojarzenia z obszarem nazw określonym w `Uri` atrybucie. Nie używaj `Prefix`pustego pliku .|
|`Query`|Parametr `String` opcjonalny.<br /><br /> Określa kwerendę XPath.|
|`Value`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa wartość, która ma zostać wstawiona do określonej ścieżki.|
|`XmlInputPath`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa dane wejściowe XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Oto sample.xml do zmodyfikowania:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

W tym przykładzie, jeśli `/Package/mp:PhoneIdentity/PhonePublisherId`chcesz zmodyfikować, użyj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn`jest tutaj używany jako prefiks sztucznej przestrzeni nazw dla domyślnej przestrzeni nazw.

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
