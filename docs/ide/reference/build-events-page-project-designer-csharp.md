---
title: Strona Zdarzenia kompilacji, Projektant projektu (C#)
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596882"
---
# <a name="build-events-page-project-designer-c"></a>Strona Zdarzenia kompilacji, Projektant projektu (C#)

Użyj **strony Zdarzenia kompilacji** **projektanta projektu,** aby określić instrukcje konfiguracji kompilacji. Można również określić warunki, w których są uruchamiane wszystkie zdarzenia po kompilacji. Aby uzyskać więcej informacji, zobacz [Jak: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md) i [jak: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista elementów UI

**Konfiguracja**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platforma**

Ta kontrolka nie jest edytowalna na tej stronie. Aby uzyskać opis tego formantu, zobacz [Strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Wiersz polecenia zdarzenia przed kompilacją**

Określa wszystkie polecenia do wykonania przed rozpoczęciem kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj wstępnie skompilować,** aby wyświetlić [okno dialogowe Wiersz polecenia zdarzenia przed kompilacją/po utworzeniu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i nie zostanie wyzwolona żadna kompilacja.

**Wiersz polecenia zdarzenia po kompilacji**

Określa wszystkie polecenia do wykonania po zakończeniu kompilacji. Aby wpisać długie polecenia, kliknij przycisk **Edytuj post-build,** aby wyświetlić **okno dialogowe Wiersz polecenia zdarzenia przed kompilacją/po utworzeniu**.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki .bat. Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Uruchamianie zdarzenia po kompilacji**

Określa następujące warunki uruchamiania zdarzenia po kompilacji, jak pokazano w poniższej tabeli.

|Opcja|Wynik|
|------------|------------|
|**Zawsze**|Zdarzenie po kompilacji zostanie uruchomione niezależnie od tego, czy kompilacja zakończy się pomyślnie.|
|**Na udanej kompilacji**|Zdarzenie po kompilacji zostanie uruchomione, jeśli kompilacja zakończy się pomyślnie. W związku z tym zdarzenie zostanie uruchomione nawet dla projektu, który jest aktualny, tak długo, jak kompilacja powiedzie się.|
|**Gdy kompilacja aktualizuje dane wyjściowe projektu**|Zdarzenie po kompilacji będzie uruchamiane tylko wtedy, gdy plik wyjściowy kompilatora (exe lub .dll) różni się od poprzedniego pliku wyjściowego kompilatora. W związku z tym zdarzenie po kompilacji nie jest uruchamiany, jeśli projekt jest aktualny.|

## <a name="in-the-project-file"></a>W pliku projektu

We wcześniejszych wersjach programu Visual Studio po zmianie **ustawienia PreBuildEvent** lub **PostBuildEvent** w środowisku IDE program Visual Studio dodaje `PreBuildEvent` lub `PostBuildEvent` właściwość do pliku projektu. Na przykład, jeśli ustawienie wiersza polecenia **PreBuildEvent** w IDE jest następujące:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

następnie ustawienie pliku projektu jest:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

W przypadku projektów .NET Core program Visual Studio 2019 (i Visual Studio 2017 `PreBuild` `PostBuild` w nowszych aktualizacjach) dodaje obiekt docelowy MSBuild o nazwie lub dla ustawień **PreBuildEvent** i **PostBuildEvent.** Te obiekty docelowe używają **BeforeTargets** i **AfterTargets** atrybuty, które MSBuild rozpoznaje. Na przykład w poprzednim przykładzie visual studio generuje teraz następujący kod:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

W przypadku zdarzenia po kompilacji `PostBuild` użyj nazwy `AfterTargets` i `PostBuildEvent`ustaw atrybut na .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Te zmiany w pliku projektu zostały wprowadzone do obsługi projektów w stylu SDK. W przypadku migracji pliku projektu ze starego formatu do formatu w stylu SDK należy `PreBuildEvent` ręcznie usunąć właściwości i `PostBuildEvent` właściwości oraz zastąpić `PreBuild` je i `PostBuild` obiekty docelowe, jak pokazano w poprzednim kodzie. Aby dowiedzieć się, jak sprawdzić, czy projekt jest projektem w stylu SDK, zobacz [Sprawdzanie formatu projektu](/nuget/resources/check-project-format).

## <a name="see-also"></a>Zobacz też

- [Porady: określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Porady: określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
