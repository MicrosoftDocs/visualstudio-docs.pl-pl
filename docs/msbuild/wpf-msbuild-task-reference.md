---
title: Odwołanie do zadania WPF MSBuild | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630850"
---
# <a name="wpf-msbuild-task-reference"></a>Odwołanie do zadania WPF MSBuild

Proces kompilacji Windows Presentation Foundation (WPF) rozszerza aparat kompilacji firmy Microsoft (MSBuild) o dodatkowy zestaw zadań kompilacji, w tym zadania do kompilowania znaczników i przetwarzania zasobów.

## <a name="in-this-section"></a>W tej sekcji

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Klasyfikuje zestaw zasobów źródłowych jako te, które zostaną osadzone w zestawie. Jeśli zasób nie jest zlokalizowany, jest osadzony w głównym zestawie aplikacji; w przeciwnym razie jest osadzony w zestawie satelicie.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Generuje zestaw, jeśli co najmniej jedna strona XAML w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub jeśli proces kompilacji zakończy się niepowodzeniem.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Zwraca katalog bieżącego środowiska uruchomieniowego programu .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Konwertuje nielokalizowalne pliki projektu XAML na skompilowany format binarny.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Wykonuje kompilację znaczników drugiego przebiegu w plikach XAML, które odwołują się do typów w tym samym projekcie.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Scala atrybuty lokalizacji i komentarze jednego lub więcej plików formatu binarnego XAML w jeden plik dla całego zestawu.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Osadza jeden lub więcej zasobów (*.jpg*, *.ico*, *.bmp*, XAML w formacie binarnym i innych typów rozszerzeń) do pliku *.resources.*

- [UidManager](../msbuild/uidmanager-task.md)

 Sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby zlokalizować wszystkie elementy XAML, które są zawarte w źródłowych plikach XAML.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Dodaje ** \<hostInBrowser />** element do manifestu aplikacji (*\<projectname>.exe.manifest)* po zbudowaniu projektu aplikacji przeglądarki XAML (XBAP).

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)