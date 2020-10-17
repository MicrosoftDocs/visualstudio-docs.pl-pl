---
title: Strona Zdarzenia kompilacji, Projektant projektu (C#)
description: Dowiedz się, jak określić instrukcje dotyczące konfiguracji kompilacji. Możesz również określić warunki, w których są uruchamiane wszystkie zdarzenia po kompilacji.
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f70557338a48931a3d109f345714d219f428f50
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136852"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)

Użyj strony **zdarzenia kompilacji** **projektanta projektu** , aby określić instrukcje konfiguracji kompilacji. Możesz również określić warunki, w których są uruchamiane wszystkie zdarzenia po kompilacji. Aby uzyskać więcej informacji, zobacz [How to: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md) i [instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista elementów UI

**Konfiguracja**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platforma**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [stronę Kompilacja, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Wiersz polecenia zdarzenia przed kompilacją**

Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij opcję **Edytuj przed kompilacją** , aby wyświetlić okno [dialogowe zdarzenie sprzed kompilacji/zdarzenie po kompilacji](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

**Wiersz polecenia zdarzenia po kompilacji**

Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj po kompilacji** , aby wyświetlić okno **dialogowe zdarzenie przed kompilacją/zdarzenie po kompilacji**.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Uruchom zdarzenie po kompilacji**

Określa następujące warunki dla zdarzenia po kompilacji do uruchomienia, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Always** (Zawsze)|Zdarzenie po kompilacji zostanie uruchomione bez względu na to, czy kompilacja powiodła się.|
|**Po pomyślnej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. W tym celu zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, o ile kompilacja zakończy się powodzeniem.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji zostanie uruchomione tylko wtedy, gdy plik wyjściowy kompilatora (. exe lub. dll) różni się od poprzedniego pliku wyjściowego kompilatora. W rezultacie zdarzenie po kompilacji nie jest uruchamiane, jeśli projekt jest aktualny.|

## <a name="in-the-project-file"></a>W pliku projektu

W starszych wersjach programu Visual Studio, gdy zmienisz ustawienie **PreBuildEvent** lub **PostBuildEvent** w IDE, Visual Studio dodaje `PreBuildEvent` `PostBuildEvent` Właściwość lub do pliku projektu. Jeśli na przykład ustawienie wiersza polecenia **PreBuildEvent** w IDE jest następujące:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

następnie ustawienie pliku projektu to:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

W przypadku projektów platformy .NET Core program Visual Studio 2019 (i program Visual Studio 2017 w nowszych aktualizacjach) dodaje element docelowy programu MSBuild o nazwie `PreBuild` lub `PostBuild` dla ustawień **PreBuildEvent** i **PostBuildEvent** . Te obiekty docelowe używają atrybutów **BeforeTargets** i **AfterTargets** , które są rozpoznawane przez program MSBuild. Na przykład w poprzednim przykładzie program Visual Studio generuje teraz następujący kod:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Dla zdarzenia po kompilacji Użyj nazwy `PostBuild` i ustaw atrybut `AfterTargets` na `PostBuildEvent` .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Te zmiany pliku projektu zostały wprowadzone do obsługi projektów w stylu zestawu SDK. Jeśli migrujesz plik projektu ze starego formatu do formatu w stylu zestawu SDK ręcznie, Usuń `PreBuildEvent` `PostBuildEvent` właściwości i zastąp je `PreBuild` `PostBuild` elementami docelowymi, jak pokazano w powyższym kodzie. Aby dowiedzieć się, jak stwierdzić, czy projekt jest projektem w stylu zestawu SDK, zobacz [Sprawdzanie projektu format](/nuget/resources/check-project-format).

## <a name="see-also"></a>Zobacz też

- [Porady: określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Porady: określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
