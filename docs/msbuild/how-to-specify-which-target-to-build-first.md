---
title: 'Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania | Microsoft Docs'
description: Dowiedz się, jak określić początkowe cele lub domyślne obiekty docelowe do skompilowania najpierw w plikach projektu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f41c9fec5b5ce9b6e4716c83edf9cd9f43e0eb94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914212"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania

Plik projektu może zawierać jeden lub więcej `Target` elementów, które definiują sposób kompilowania projektu. Aparat Microsoft Build Engine (MSBuild) kompiluje pierwszy znaleziony obiekt docelowy i wszelkie zależności, chyba że plik projektu zawiera `DefaultTargets` atrybut, `InitialTargets` atrybut lub element docelowy jest określony w wierszu polecenia przy użyciu przełącznika **-Target** .
## <a name="use-the-initialtargets-attribute"></a>Użyj atrybutu InitialTargets

`InitialTargets`Atrybut `Project` elementu określa element docelowy, który zostanie uruchomiony jako pierwszy, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybucie.

#### <a name="to-specify-one-initial-target"></a>Aby określić jeden początkowy element docelowy

- Określ domyślny cel w `InitialTargets` atrybucie `Project` elementu. Na przykład:

   `<Project InitialTargets="Clean">`

  Można określić więcej niż jeden początkowy element docelowy w `InitialTargets` atrybucie, wyświetlając listę elementów docelowych w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.

#### <a name="to-specify-more-than-one-initial-target"></a>Aby określić więcej niż jeden początkowy element docelowy

- Utwórz listę początkowych elementów docelowych rozdzielonych średnikami, w `InitialTargets` atrybucie `Project` elementu. Na przykład, aby uruchomić `Clean` obiekt docelowy, a następnie `Compile` element docelowy, wpisz:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Użyj atrybutu DefaultTargets —

 `DefaultTargets`Atrybut `Project` elementu określa, które elementy docelowe lub docelowe są kompilowane, jeśli element docelowy nie zostanie jawnie określony w wierszu polecenia. Jeśli obiekty docelowe są określone w `InitialTargets` `DefaultTargets` atrybutach i i nie określono elementu docelowego w wierszu polecenia, MSBuild uruchamia elementy docelowe określone w atrybucie, `InitialTargets` a następnie obiekty docelowe określone w `DefaultTargets` atrybucie.

#### <a name="to-specify-one-default-target"></a>Aby określić jeden domyślny obiekt docelowy

- Określ domyślny cel w `DefaultTargets` atrybucie `Project` elementu. Na przykład:

   `<Project DefaultTargets="Compile">`

  Można określić więcej niż jeden domyślny obiekt docelowy w `DefaultTargets` atrybucie, wyświetlając listę elementów docelowych w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.

#### <a name="to-specify-more-than-one-default-target"></a>Aby określić więcej niż jeden domyślny obiekt docelowy

- Utwórz listę domyślnych obiektów docelowych oddzielonych średnikami, w `DefaultTargets` atrybucie `Project` elementu. Na przykład, aby uruchomić `Clean` obiekt docelowy, a następnie `Compile` element docelowy, wpisz:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Użyj przełącznika-Target

 Jeśli domyślny element docelowy nie jest zdefiniowany w pliku projektu lub jeśli nie chcesz używać tego domyślnego obiektu docelowego, możesz użyć przełącznika wiersza polecenia **-Target** , aby określić inny element docelowy. Element docelowy lub docelowy określone za pomocą przełącznika **-Target** są uruchamiane zamiast elementów docelowych określonych przez `DefaultTargets` atrybut. Elementy docelowe określone w `InitialTargets` atrybucie zawsze są uruchamiane jako pierwsze.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Aby użyć elementu docelowego innego niż domyślny obiekt docelowy

- Określ element docelowy jako pierwszy element docelowy przy użyciu przełącznika wiersza polecenia **-Target** . Na przykład:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Aby użyć kilku obiektów docelowych, które są inne niż domyślne elementy docelowe

- Utwórz listę elementów docelowych rozdzielonych średnikami lub przecinkami przy użyciu przełącznika wiersza polecenia **-Target** . Na przykład:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
- [Instrukcje: czyszczenie kompilacji](../msbuild/how-to-clean-a-build.md)
