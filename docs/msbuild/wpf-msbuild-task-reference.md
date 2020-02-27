---
title: Odwołanie do zadania WPF MSBuild | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630850"
---
# <a name="wpf-msbuild-task-reference"></a>Odwołanie do zadania WPF MSBuild

Proces kompilacji Windows Presentation Foundation (WPF) rozszerza program Microsoft Build Engine (MSBuild) z dodatkowym zestawem zadań kompilacji, w tym zadaniami do kompilowania znaczników i zasobów procesów.

## <a name="in-this-section"></a>W tej sekcji

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Klasyfikuje zestaw zasobów źródłowych jako te, które będą osadzone w zestawie. Jeśli zasób nie jest Lokalizowalny, jest osadzony w głównym zestawie aplikacji; w przeciwnym razie jest osadzony w zestawie satelickim.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Generuje zestaw, jeśli co najmniej jedna strona XAML w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub w przypadku niepowodzenia procesu kompilacji.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Zwraca katalog bieżącego .NET Framework środowiska uruchomieniowego.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Konwertuje nielokalizowalne pliki projektu XAML na skompilowany format binarny.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Wykonuje kompilację drugiego przebiegu znaczników dla plików XAML, które odwołują się do typów w tym samym projekcie.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Scala atrybuty lokalizacji i komentarze jednego lub więcej plików formatu binarnego XAML do pojedynczego pliku dla całego zestawu.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Osadza jeden lub więcej zasobów ( *. jpg*, *. ico*, *. bmp*, XAML w formacie binarnym i innych typów rozszerzenia) w pliku *resources* .

- [UidManager](../msbuild/uidmanager-task.md)

 Sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID) w celu zlokalizowania wszystkich elementów XAML, które są zawarte w źródłowym pliku XAML.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Dodaje **\<HostInBrowser/>** do manifestu aplikacji ( *\<ProjectName >. exe. manifest*) podczas kompilowania projektu aplikacji przeglądarki XAML (XBAP).

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)