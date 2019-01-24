---
title: Odwołanie do zadania MSBuild WPF | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 51a052dea0a828201400086e25880124cb4a05c1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776986"
---
# <a name="wpf-msbuild-task-reference"></a>Odwołanie do zadania WPF MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Proces kompilacji Windows Presentation Foundation (WPF) Microsoft build engine (MSBuild) rozszerza możliwości za sprawą dodatkowego zestawu zadań kompilacji, w tym zadania, aby skompilować i zasobów procesowych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klasyfikuje zestaw zasobów źródłowego, jak te, które zostaną osadzone w zestawie. Jeśli zasób nie jest możliwych do zlokalizowania, jest osadzony w głównym zestawem aplikacji; w przeciwnym razie jest osadzony w zestawie satelickim.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generuje zestaw, jeśli co najmniej jeden [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] strony w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowanego zestawu jest usuwany po zakończeniu procesu kompilacji, czy Proces kompilacji zakończy się niepowodzeniem.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Zwraca katalog bieżącego [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] środowiska uruchomieniowego.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Konwertuje niemożliwe do zlokalizowania [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] pliki na skompilowany format binarny projektu.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Przeprowadza korektę znaczników kompilacji na [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] pliki, które odwołują się typy w tym samym projekcie.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Scala atrybuty lokalizacji i komentarze, co najmniej jednego [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików binarnych w jeden plik dla całego zestawu.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Osadza co najmniej jeden zasób (.ico jpg, bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym, a inne typy rozszerzeń) do pliku Resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Sprawdza, czy, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby zlokalizować wszystkie [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] elementy, które znajdują się w źródle [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Dodaje  **\<hostInBrowser / >** elementu w manifeście aplikacji (*projectname*. exe.manifest) podczas [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] projekt został skompilowany.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild](http://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
