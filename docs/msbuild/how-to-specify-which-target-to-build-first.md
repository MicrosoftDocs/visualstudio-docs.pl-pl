---
title: 'Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania | Microsoft Docs'
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
ms.openlocfilehash: 75bcb41bb2df2afcb6e71b0fdaf58d0d7429e974
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574631"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania
Plik projektu może zawierać jeden lub więcej elementów `Target`, które definiują sposób kompilowania projektu. Silnik [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) kompiluje pierwszy znaleziony projekt i wszelkie zależności, chyba że plik projektu zawiera atrybut `DefaultTargets`, atrybut `InitialTargets` lub element docelowy jest określony w wierszu polecenia przy użyciu przełącznika **-Target** .

## <a name="use-the-initialtargets-attribute"></a>Użyj atrybutu InitialTargets
 Atrybut `InitialTargets` elementu `Project` określa element docelowy, który zostanie uruchomiony jako pierwszy, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w atrybucie `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Aby określić jeden początkowy element docelowy

- Określ domyślny cel w atrybucie `InitialTargets` elementu `Project`. Na przykład:

   `<Project InitialTargets="Clean">`

  Można określić więcej niż jeden początkowy element docelowy w atrybucie `InitialTargets`, wymieniając elementy docelowe w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.

#### <a name="to-specify-more-than-one-initial-target"></a>Aby określić więcej niż jeden początkowy element docelowy

- Utwórz listę początkowych elementów docelowych rozdzielonych średnikami, w atrybucie `InitialTargets` elementu `Project`. Na przykład, aby uruchomić `Clean` cel, a następnie element docelowy `Compile`, wpisz:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Użyj atrybutu DefaultTargets —
 Atrybut `DefaultTargets` elementu `Project` określa, które elementy docelowe lub docelowe są kompilowane, jeśli element docelowy nie zostanie jawnie określony w wierszu polecenia. Jeśli obiekty docelowe są określone zarówno w atrybucie `InitialTargets`, jak i `DefaultTargets` i nie określono elementu docelowego w wierszu polecenia, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uruchamia obiekty docelowe określone w atrybut `InitialTargets`, a następnie obiekty docelowe określone w atrybucie `DefaultTargets`.

#### <a name="to-specify-one-default-target"></a>Aby określić jeden domyślny obiekt docelowy

- Określ domyślny cel w atrybucie `DefaultTargets` elementu `Project`. Na przykład:

   `<Project DefaultTargets="Compile">`

  Można określić więcej niż jeden domyślny obiekt docelowy w atrybucie `DefaultTargets`, wymieniając elementy docelowe w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.

#### <a name="to-specify-more-than-one-default-target"></a>Aby określić więcej niż jeden domyślny obiekt docelowy

- Utwórz listę domyślnych obiektów docelowych oddzielonych średnikami, w atrybucie `DefaultTargets` elementu `Project`. Na przykład, aby uruchomić `Clean` cel, a następnie element docelowy `Compile`, wpisz:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Użyj przełącznika-Target
 Jeśli domyślny element docelowy nie jest zdefiniowany w pliku projektu lub jeśli nie chcesz używać tego domyślnego obiektu docelowego, możesz użyć przełącznika wiersza polecenia **-Target** , aby określić inny element docelowy. Element docelowy lub docelowy określone za pomocą przełącznika **-Target** są uruchamiane zamiast obiektów docelowych określonych przez atrybut `DefaultTargets`. Elementy docelowe określone w atrybucie `InitialTargets` zawsze są uruchamiane jako pierwsze.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Aby użyć elementu docelowego innego niż domyślny obiekt docelowy

- Określ element docelowy jako pierwszy element docelowy przy użyciu przełącznika wiersza polecenia **-Target** . Na przykład:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Aby użyć kilku obiektów docelowych, które są inne niż domyślne elementy docelowe

- Utwórz listę elementów docelowych rozdzielonych średnikami lub przecinkami przy użyciu przełącznika wiersza polecenia **-Target** . Na przykład:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
- [Docelowe elementy](../msbuild/msbuild-targets.md)
- [Instrukcje: czyszczenie kompilacji](../msbuild/how-to-clean-a-build.md)
