---
title: Zadanie CallTarget | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094560"
---
# <a name="calltarget-task"></a>CallTarget — zadanie

Wywołuje określone obiekty docelowe w pliku projektu.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `CallTarget` opisano parametry zadania.

| Parametr | Opis |
|---------------------------| - |
| `RunEachTargetSeparately` | Opcjonalny `Boolean` parametr wejściowy.<br /><br /> Jeśli `true`aparat MSBuild jest wywoływany raz na obiekt docelowy. Jeśli `false`aparat MSBuild jest wywoływana raz do tworzenia wszystkich obiektów docelowych. Wartością domyślną jest `false`. |
| `TargetOutputs` | Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera dane wyjściowe wszystkich obiektów docelowych zbudowanych. |
| `Targets` | Parametr `String[]` opcjonalny.<br /><br /> Określa obiekt docelowy lub cele do zbudowania. |
| `UseResultsCache` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`wynik buforowany jest zwracany, jeśli jest obecny.<br /><br /> **Uwaga** Po uruchomieniu zadania MSBuild jego dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties)[TargetNames] jako lista elementów kompilacji. |

## <a name="remarks"></a>Uwagi

 Jeśli cel określony `Targets` w `RunEachTargetSeparately` `true`nie powiedzie się i jest , zadanie kontynuuje tworzenie pozostałych obiektów docelowych.

 Jeśli chcesz zbudować domyślne obiekty docelowe, użyj [zadania MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` parametr równy . `$(MSBuildProjectFile)`

Podczas `CallTarget`korzystania z , MSBuild ocenia o nazwie docelowej w nowym zakresie, w przeciwieństwie do tego samego zakresu jest wywoływana z. Oznacza to, że wszelkie zmiany elementu i właściwości w o nazwie docelowej nie są widoczne dla obiektu docelowego wywołującego.  Aby przekazać informacje do obiektu `TargetOutputs` docelowego wywołującego, należy użyć parametru wyjściowego.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład `TargetA` wywołuje `CallOtherTargets`od wewnątrz .

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Cele](../msbuild/msbuild-targets.md)
