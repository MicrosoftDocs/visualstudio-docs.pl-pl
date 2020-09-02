---
title: Odwołanie do zadania WPF MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb21495954801d55c1db0bb9156a813ab73db683
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687099"
---
# <a name="wpf-msbuild-task-reference"></a>Odwołanie do zadania WPF MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces kompilacji Windows Presentation Foundation (WPF) rozszerza program Microsoft Build Engine (MSBuild) z dodatkowym zestawem zadań kompilacji, w tym zadaniami do kompilowania znaczników i zasobów procesów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klasyfikuje zestaw zasobów źródłowych jako te, które będą osadzone w zestawie. Jeśli zasób nie jest Lokalizowalny, jest osadzony w głównym zestawie aplikacji; w przeciwnym razie jest osadzony w zestawie satelickim.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generuje zestaw, jeśli co najmniej jedna [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Strona w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub w przypadku niepowodzenia procesu kompilacji.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Zwraca katalog bieżącego [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] środowiska uruchomieniowego.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Konwertuje nielokalizowalne [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] pliki projektu na skompilowany format binarny.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Wykonuje kompilację drugiego przebiegu znaczników dla [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] plików, które odwołują się do typów w tym samym projekcie.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Scala atrybuty lokalizacji i komentarze jednego lub więcej [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików formatu binarnego w pojedynczym pliku dla całego zestawu.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Osadza jeden lub więcej zasobów (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym i innych typów rozszerzenia) w pliku Resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID) w celu zlokalizowania wszystkich [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] elementów uwzględnionych w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plikach źródłowych.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Dodaje **\<hostInBrowser />** element do manifestu aplikacji (*ProjectName*. exe. manifest) podczas [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] kompilowania projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
