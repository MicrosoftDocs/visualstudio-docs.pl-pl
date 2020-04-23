---
title: 'Jak: Określ, który cel zbudować jako pierwszy | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7656237be5cf7906293a294885cfa3e6c8bd4e36
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072531"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Jak: Określ, który cel ma być najpierw zbudowany

Plik projektu może zawierać `Target` jeden lub więcej elementów, które definiują sposób budowy projektu. Aparat microsoft build engine (MSBuild) tworzy pierwszy obiekt docelowy, który znajdzie, `DefaultTargets` a wszelkie `InitialTargets` zależności, chyba że plik projektu zawiera atrybut, atrybut lub obiekt docelowy jest określony w wierszu polecenia przy użyciu przełącznika **-target.**
## <a name="use-the-initialtargets-attribute"></a>Użyj atrybutu InitialTargets

Atrybut `InitialTargets` `Project` elementu określa obiekt docelowy, który zostanie uruchomiony jako pierwszy, nawet jeśli `DefaultTargets` obiekty docelowe są określone w wierszu polecenia lub w atrybucie.

#### <a name="to-specify-one-initial-target"></a>Aby określić jeden początkowy cel

- Określ domyślny `InitialTargets` obiekt docelowy `Project` w atrybucie elementu. Przykład:

   `<Project InitialTargets="Clean">`

  Można określić więcej niż jeden `InitialTargets` początkowy cel w atrybucie, wymieniając obiekty docelowe w kolejności i używając średnika do oddzielenia każdego obiektu docelowego. Obiekty docelowe na liście będą uruchamiane sekwencyjnie.

#### <a name="to-specify-more-than-one-initial-target"></a>Aby określić więcej niż jeden początkowy cel

- Lista początkowych celów, oddzielone średnikami, `InitialTargets` w atrybucie `Project` elementu. Na przykład, aby `Clean` uruchomić obiekt `Compile` docelowy, a następnie miejsce docelowe, wpisz:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Używanie atrybutu DefaultTargets

 Atrybut `DefaultTargets` `Project` elementu określa, który obiekt docelowy lub obiekty docelowe są budowane, jeśli obiekt docelowy nie jest wyraźnie określony w wierszu polecenia. Jeśli obiekty docelowe `InitialTargets` są `DefaultTargets` określone zarówno w i atrybuty i nie ma obiektu docelowego jest określony w wierszu polecenia, MSBuild uruchamia obiekty docelowe określone w `InitialTargets` atrybucie, a następnie cele określone w `DefaultTargets` atrybucie.

#### <a name="to-specify-one-default-target"></a>Aby określić jeden domyślny cel

- Określ domyślny `DefaultTargets` obiekt docelowy `Project` w atrybucie elementu. Przykład:

   `<Project DefaultTargets="Compile">`

  Można określić więcej niż jeden `DefaultTargets` domyślny cel w atrybucie, wymieniając obiekty docelowe w kolejności i używając średnika do oddzielenia każdego obiektu docelowego. Obiekty docelowe na liście będą uruchamiane sekwencyjnie.

#### <a name="to-specify-more-than-one-default-target"></a>Aby określić więcej niż jeden domyślny cel

- Lista domyślnych obiektów docelowych, oddzielone `DefaultTargets` średnikami, `Project` w atrybucie elementu. Na przykład, aby `Clean` uruchomić obiekt `Compile` docelowy, a następnie miejsce docelowe, wpisz:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Korzystanie z przełącznika -target

 Jeśli domyślny cel nie jest zdefiniowany w pliku projektu lub jeśli nie chcesz używać tego domyślnego obiektu docelowego, możesz użyć przełącznika wiersza polecenia **-target,** aby określić inny cel. Obiekt docelowy lub obiekty docelowe określone za pomocą przełącznika `DefaultTargets` **-target** są uruchamiane zamiast obiektów docelowych określonych przez atrybut. Obiekty docelowe `InitialTargets` określone w atrybucie zawsze są uruchamiane jako pierwsze.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Aby najpierw użyć celu innego niż domyślny cel

- Określ obiekt docelowy jako pierwszy obiekt docelowy za pomocą przełącznika **-target** wiersza polecenia. Przykład:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Aby najpierw użyć kilku celów innych niż domyślne cele

- Wymień obiekty docelowe oddzielone średnikami lub przecinkami za pomocą przełącznika **-target** command line. Przykład:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
- [Cele](../msbuild/msbuild-targets.md)
- [Jak: Czyszczenie kompilacji](../msbuild/how-to-clean-a-build.md)
