---
title: Obsługa Ngen w VSIX v3 | Dokumenty firmy Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702402"
---
# <a name="ngen-support-in-vsix-v3"></a>Obsługa Ngen w rozszerzeniu VSIX v3

Dzięki programowi Visual Studio 2017 i nowemu formatowi manifestu rozszerzenia VSIX w wersji 3 (wersja 3) deweloperzy rozszerzeń mogą teraz "ngen" ich zestawów w czasie instalacji.

Poniżej znajduje się fragment z MSDN, który wyjaśnia, co "ngen" nie:

>Native Image Generator *(Ngen.exe)* jest narzędziem, które poprawia wydajność zarządzanych aplikacji. *Program Ngen.exe* tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w natywnej pamięci podręcznej obrazów na komputerze lokalnym. Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.
>
>od [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Aby "ngen" zestaw, VSIX musi być zainstalowany "na wystąpienie na komputerze". Można to włączyć, zaznaczając pole wyboru "wszyscy użytkownicy" w projektancie: `extension.vsixmanifest`

![sprawdź wszystkich użytkowników](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Jak włączyć Ngen

Aby włączyć ngen dla zestawu, można użyć **właściwości** okna w programie Visual Studio.

Istnieją 4 właściwości, które można ustawić:

1. **Ngen** (Boolean) - Jeśli true, Instalator programu Visual Studio będzie "ngen" zestawu.
2. **Ngen application** (string) - Ngen zapewnia możliwość korzystania z pliku *app.config* aplikacji w celu rozwiązania zależności zestawu. Ta wartość powinna być ustawiona na aplikację, której *app.config* chcesz użyć (względem katalogu instalacji programu Visual Studio).
3. **Ngen Architecture** (wyliczenia) - architektura do natywnie skompilować zestawu. Dostępne opcje to: a. NotSpecyfikowany b. X86 c. X64 d. Wszystkie
4. **Ngen Priority** (liczba całkowita między 1 a 3) - Poziom priorytetu Ngen jest udokumentowany na [poziomach priorytetu Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Oto spojrzenie na **właściwości** okna w akcji:

![ngen w właściwościach](media/ngen-in-properties.png)

Spowoduje to dodanie metadanych do odwołania do projektu wewnątrz pliku *csproj* projektu VSIX:

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
> Jeśli wolisz, możesz edytować plik csproj.

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości dotyczą więcej niż tylko odwołań do projektu; można ustawić metadane Ngen dla elementów wewnątrz projektu, jak również (przy użyciu tych samych metod opisanych powyżej), tak długo, jak elementy są .NET zestawy.
