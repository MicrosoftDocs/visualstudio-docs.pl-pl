---
title: Obsługa NGen w VSIX v3 | Microsoft Docs
description: Dowiedz się, jak włączyć Generator obrazu natywnego, czyli narzędzie, którego deweloperzy mogą używać do ulepszania wydajności aplikacji zarządzanych.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864029"
---
# <a name="ngen-support-in-vsix-v3"></a>Obsługa Ngen w rozszerzeniu VSIX v3

Dzięki programowi Visual Studio 2017 i nowemu formatowi manifestu rozszerzenia VSIX v3 (wersja 3), deweloperzy rozszerzeń mogą teraz "NGen" w czasie instalacji.

Poniżej znajduje się fragment z witryny MSDN, który wyjaśnia, co to jest "NGen":

>Generator obrazu natywnego (*Ngen.exe*) to narzędzie, które poprawia wydajność zarządzanych aplikacji. *Ngen.exe* tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.
>
>z [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Aby "NGen" zestaw, należy zainstalować plik VSIX "na wystąpienie dla każdego komputera". Tę funkcję można włączyć, zaznaczając pole wyboru "Wszyscy użytkownicy" w `extension.vsixmanifest` projektancie:

![Zaznacz wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak włączyć program Ngen

Aby włączyć program Ngen dla zestawu, można użyć okna **Właściwości** w programie Visual Studio.

Dostępne są 4 właściwości, które można ustawić:

1. **NGen** (wartość logiczna) — w przypadku wartości true Instalator programu Visual Studio będzie "NGen" zestawu.
2. **Aplikacja NGen** (ciąg) — program Ngen umożliwia korzystanie z pliku *app.config* aplikacji w celu rozpoznania zależności zestawu. Ta wartość powinna być ustawiona na aplikację, której *app.config* chcesz użyć (względem katalogu instalacyjnego programu Visual Studio).
3. **Architektura NGen** (enum) — architektura do natywnego kompilowania zestawu. Dostępne są następujące opcje: a. NotSpecified b. X86 c. X64 d. Wszystko
4. **Priorytet NGen** (liczba całkowita z zakresu od 1 do 3) — poziom priorytetu NGEN jest udokumentowany na [ poziomach priorytetuNgen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Sprawdź okno **Właściwości** w akcji:

![NGen w właściwościach](media/ngen-in-properties.png)

Spowoduje to dodanie metadanych do odwołania projektu w pliku *. csproj* projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Plik. csproj można edytować bezpośrednio, jeśli wolisz.

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości dotyczą więcej niż tylko odwołań projektu; można również ustawić metadane NGen dla elementów wewnątrz projektu (przy użyciu tych samych metod opisanych powyżej), o ile elementy są zestawami .NET.
