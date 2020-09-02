---
title: 'Instrukcje: Określanie pierwszego obiektu docelowego do skompilowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178341"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Porady: określanie pierwszego obiektu docelowego do kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plik projektu może zawierać jeden lub więcej `Target` elementów, które definiują sposób kompilowania projektu. [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]Aparat ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) kompiluje pierwszy znaleziony projekt i wszelkie zależności, chyba że plik projektu zawiera `DefaultTargets` atrybut, `InitialTargets` atrybut lub element docelowy jest określony w wierszu polecenia przy użyciu przełącznika **/Target** .  
  
## <a name="using-the-initialtargets-attribute"></a>Korzystanie z atrybutu InitialTargets  
 `InitialTargets`Atrybut `Project` elementu określa element docelowy, który zostanie uruchomiony jako pierwszy, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybucie.  
  
#### <a name="to-specify-one-initial-target"></a>Aby określić jeden początkowy element docelowy  
  
- Określ domyślny cel w `InitialTargets` atrybucie `Project` elementu. Na przykład:  
  
   `<Project InitialTargets="Clean">`  
  
  Można określić więcej niż jeden początkowy element docelowy w `InitialTargets` atrybucie, wyświetlając listę elementów docelowych w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Aby określić więcej niż jeden początkowy element docelowy  
  
- Utwórz listę początkowych elementów docelowych rozdzielonych średnikami, w `InitialTargets` atrybucie `Project` elementu. Na przykład, aby uruchomić `Clean` obiekt docelowy, a następnie `Compile` element docelowy, wpisz:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Korzystanie z atrybutu DefaultTargets —  
 `DefaultTargets`Atrybut `Project` elementu określa, które elementy docelowe lub docelowe są kompilowane, jeśli element docelowy nie zostanie jawnie określony w wierszu polecenia. Jeśli obiekty docelowe są określone w atrybutach `InitialTargets` i `DefaultTargets` i nie określono elementu docelowego w wierszu polecenia, program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] uruchamia elementy docelowe określone w `InitialTargets` atrybucie, a następnie obiekty docelowe określone w `DefaultTargets` atrybucie.  
  
#### <a name="to-specify-one-default-target"></a>Aby określić jeden domyślny obiekt docelowy  
  
- Określ domyślny cel w `DefaultTargets` atrybucie `Project` elementu. Na przykład:  
  
   `<Project DefaultTargets="Compile">`  
  
  Można określić więcej niż jeden domyślny obiekt docelowy w `DefaultTargets` atrybucie, wyświetlając listę elementów docelowych w kolejności i używając średnika, aby oddzielić każdy element docelowy. Elementy docelowe na liście zostaną uruchomione sekwencyjnie.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Aby określić więcej niż jeden domyślny obiekt docelowy  
  
- Utwórz listę domyślnych obiektów docelowych oddzielonych średnikami, w `DefaultTargets` atrybucie `Project` elementu. Na przykład, aby uruchomić `Clean` obiekt docelowy, a następnie `Compile` element docelowy, wpisz:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Korzystanie z przełącznika/Target  
 Jeśli domyślny element docelowy nie jest zdefiniowany w pliku projektu lub jeśli nie chcesz używać tego domyślnego obiektu docelowego, możesz użyć polecenia **, aby określić** inny element docelowy. Element docelowy lub cel określony za pomocą przełącznika **/Target** są uruchamiane zamiast elementów docelowych określonych przez `DefaultTargets` atrybut. Elementy docelowe określone w `InitialTargets` atrybucie zawsze są uruchamiane jako pierwsze.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Aby użyć elementu docelowego innego niż domyślny obiekt docelowy  
  
- Określ cel jako pierwszy element docelowy przy użyciu przełącznika wiersza polecenia **/Target** . Na przykład:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Aby użyć kilku obiektów docelowych, które są inne niż domyślne elementy docelowe  
  
- Utwórz listę elementów docelowych rozdzielonych średnikami lub przecinkami, używając przełącznika wiersza polecenia **/Target** . Na przykład:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Zobacz też
  [MSBuild](msbuild.md)  
 [Celach](../msbuild/msbuild-targets.md)   
 [Instrukcje: Czyszczenie kompilacji](../msbuild/how-to-clean-a-build.md)
