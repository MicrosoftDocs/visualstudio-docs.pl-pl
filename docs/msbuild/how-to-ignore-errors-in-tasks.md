---
title: 'Instrukcje: ignorowanie błędów w zadaniach | Microsoft Docs'
description: Dowiedz się, jak ignorować błędy w zadaniach MSBuild i kontrolować, czy kompilacja zatrzyma się czy kontynuuje, gdy wystąpi błąd zadania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: f2c0b070868b8dc9fc10c4f493fbb75948485a5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914245"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Instrukcje: ignorowanie błędów w zadaniach

Czasami, gdy kompilacja ma być odporna na błędy w niektórych zadaniach. Jeśli te zadania niekrytyczne zakończą się niepowodzeniem, chcesz, aby kompilacja kontynuowała działanie, ponieważ nadal może generować wymagane dane wyjściowe. Na przykład, jeśli projekt używa `SendMail` zadania do wysłania wiadomości e-mail po skompilowaniu każdego składnika, można rozważyć, że może on zostać zaakceptowany do ukończenia kompilacji, nawet jeśli serwery poczty są niedostępne i nie można wysłać komunikatów o stanie. Jeśli na przykład pliki pośrednie są zazwyczaj usuwane podczas kompilacji, można rozważyć zaakceptowanie, aby kompilacja kontynuowała wykonywanie nawet wtedy, gdy te pliki nie mogą zostać usunięte.

## <a name="use-the-continueonerror-attribute"></a>Użyj atrybutu ContinueOnError

`ContinueOnError`Atrybut `Task` elementu określa, czy kompilacja jest zatrzymywana czy kontynuowana, gdy wystąpi błąd zadania. Ten atrybut określa również, czy błędy mają być traktowane jako błędy lub ostrzeżenia, gdy kompilacja będzie kontynuowana.

`ContinueOnError`Atrybut może zawierać jedną z następujących wartości:

- **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.

- **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.

- **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.

Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.

Wartość domyślna `ContinueOnError` to `ErrorAndStop` . W przypadku ustawienia atrybutu na `ErrorAndStop` , należy jawnie wprowadzić zachowanie dla każdej osoby, która odczytuje plik projektu.

#### <a name="to-ignore-an-error-in-a-task"></a>Aby zignorować błąd w zadaniu

Użyj `ContinueOnError` atrybutu zadania. Na przykład:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje, że `Build` element docelowy nadal działa i kompilacja jest uważana za sukces, nawet jeśli `Delete` zadanie nie powiedzie się.

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
