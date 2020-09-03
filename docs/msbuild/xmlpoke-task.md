---
title: XmlPoke — — zadanie | Microsoft Docs
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
ms.openlocfilehash: b69afc20d15802ad79b201ca38e2d69f1d473b1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82072510"
---
# <a name="xmlpoke-task"></a>XmlPoke — zadanie

Ustawia wartości określone przez zapytanie XPath w pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `XmlPoke` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalny `String` parametr.<br /><br /> Określa przestrzenie nazw dla prefiksów zapytania XPath. `Namespaces` jest fragmentem kodu XML składającym się z `Namespace` elementów z atrybutami `Prefix` i `Uri` . Atrybut `Prefix` Określa prefiks do skojarzenia z przestrzenią nazw określoną w `Uri` atrybucie. Nie należy używać pustego elementu `Prefix` .|
|`Query`|Opcjonalny `String` parametr.<br /><br /> Określa zapytanie XPath.|
|`Value`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa wartość, która ma zostać wstawiona do określonej ścieżki.|
|`XmlInputPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa dane wejściowe w formacie XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

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

W tym przykładzie, jeśli chcesz zmodyfikować `/Package/mp:PhoneIdentity/PhoneProductId` , użyj

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

`dn` jest używany jako prefiks sztucznej przestrzeni nazw dla domyślnej przestrzeni nazw.

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
