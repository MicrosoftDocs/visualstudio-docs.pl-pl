---
title: 'Instrukcje: Określanie pierwszego obiektu docelowego do kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc6e8ec70c941035caa0e4b3569f82013a829f15
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970581"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Instrukcje: Określ, która docelowa do tworzenia najpierw
Plik projektu może zawierać jeden lub więcej `Target` elementy, które określają jak projekt jest kompilowany. [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) Aparatu kompilacji pierwszego projektu go odnajduje i wszelkie zależności, chyba, że plik projektu zawiera `DefaultTargets` atrybutu `InitialTargets` atrybutu lub elementu docelowego jest określony w wierszu polecenia za pomocą **— docelowy** przełącznika.  
  
## <a name="use-the-initialtargets-attribute"></a>Użyj atrybutu InitialTargets  
 `InitialTargets` Atrybutu `Project` element określa obiekt docelowy, który zostanie uruchomiony po pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybutu.  
  
#### <a name="to-specify-one-initial-target"></a>Aby określić jeden element docelowy początkowej  
  
- Określ domyślny element docelowy w `InitialTargets` atrybutu `Project` elementu. Na przykład:  
  
   `<Project InitialTargets="Clean">`  
  
  Można określić więcej niż jeden początkowego elementu docelowego w `InitialTargets` atrybut Lista elementów docelowych w kolejności, a za pomocą średnika do rozdzielenia każdego obiektu docelowego. Obiekty docelowe, na liście będą uruchamiane sekwencyjnie.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Aby określić więcej niż jeden element docelowy początkowej  
  
-   Cele początkowe, oddzielone średnikami w liście `InitialTargets` atrybutu `Project` elementu. Na przykład, aby uruchomić `Clean` docelowego i następnie `Compile` obiekt docelowy, wpisz:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="use-the-defaulttargets-attribute"></a>Użyj defaulttargets — atrybut  
 `DefaultTargets` Atrybutu `Project` element określa, których cel lub cele są tworzone, jeśli element docelowy nie jest jawnie określona w wierszu polecenia. Jeśli nie określono elementów docelowych w obu `InitialTargets` i `DefaultTargets` atrybuty i żadne miejsce docelowe nie jest określona w wierszu polecenia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uruchamia obiektów docelowych określonych w `InitialTargets` atrybut następuje obiektów docelowych określonych w `DefaultTargets` atrybut.  
  
#### <a name="to-specify-one-default-target"></a>Aby określić jeden domyślny element docelowy.  
  
- Określ domyślny element docelowy w `DefaultTargets` atrybutu `Project` elementu. Na przykład:  
  
   `<Project DefaultTargets="Compile">`  
  
  Można określić więcej niż jeden domyślny element docelowy, w `DefaultTargets` atrybut Lista elementów docelowych w kolejności, a za pomocą średnika do rozdzielenia każdego obiektu docelowego. Obiekty docelowe, na liście będą uruchamiane sekwencyjnie.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Aby określić więcej niż jeden domyślny element docelowy.  
  
-   Lista domyślnych elementów docelowych, oddzielonych średnikami, w `DefaultTargets` atrybutu `Project` elementu. Na przykład, aby uruchomić `Clean` docelowego i następnie `Compile` obiekt docelowy, wpisz:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="use-the--target-switch"></a>Użyj przełącznika - target  
 Jeśli domyślny element docelowy nie jest zdefiniowana w pliku projektu lub jeśli chcesz użyć tego domyślnego obiektu docelowego, można użyć przełącznika wiersza polecenia **-target** Aby określić inny element docelowy. Cel lub cele określony za pomocą **-target** przełącznika są uruchamiane zamiast elementów docelowych określone przez `DefaultTargets` atrybutu. Obiektów docelowych określonych w `InitialTargets` są zawsze uruchamiane pierwszego atrybutu.  
 
 
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Aby użyć pierwszy element docelowy inny niż domyślny element docelowy  
  
-   Określ element docelowy jako pierwszy przy użyciu docelowej **-target** przełącznik wiersza polecenia. Na przykład:  
  
     `msbuild file.proj -target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Aby korzystać z kilku jest przeznaczony dla innych niż domyślne elementy docelowe najpierw  
  
-   Lista obiektów docelowych, rozdzielone średnikami lub przecinkami, za pomocą **-target** przełącznik wiersza polecenia. Na przykład:  
  
     `msbuild <file name>.proj -t:Clean;Compile`  
  
## <a name="see-also"></a>Zobacz także
  [MSBuild](../msbuild/msbuild.md)  
 [Obiekty docelowe](../msbuild/msbuild-targets.md)   
 [Instrukcje: Czyszczenie kompilacji](../msbuild/how-to-clean-a-build.md)
