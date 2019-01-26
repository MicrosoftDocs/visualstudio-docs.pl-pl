---
title: Xmlpoke — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 691a9ddbba4291bb6b54d15c9b60e6339b2548b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963791"
---
# <a name="xmlpoke-task"></a>XmlPoke — zadanie

Ustawia wartości określonych przez zapytanie XPath do pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `XmlPoke` zadania.
  
|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalnie `String` parametru.<br /><br /> Określa obszary nazw w przypadku prefiksów kwerendy XPath. `Namespaces` jest składający się z fragmentu kodu XML `Namespace` elementy z atrybutami `Prefix` i `Uri`. Ten atrybut `Prefix` Określa prefiks do skojarzenia z przestrzeni nazw określonej w `Uri` atrybutu. Nie używaj pustego `Prefix`.|
|`Query`|Opcjonalnie `String` parametru.<br /><br /> Określa zapytanie XPath.|
|`Value`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa wartość do wstawienia do określonej ścieżki.|
|`XmlInputPath`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę do pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Oto sample.xml, aby zmodyfikować:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

W tym przykładzie, jeśli chcesz zmodyfikować `/Package/mp:PhoneIdentity/PhonePublisherId`, następnie za pomocą

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

`dn` w tym miejscu służy jako prefiks sztuczne przestrzeni nazw dla domyślny obszar nazw.

## <a name="see-also"></a>Zobacz także

 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
