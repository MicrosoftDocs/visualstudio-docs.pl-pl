---
title: Omówienie rozwiązań
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705299"
---
# <a name="solutions-overview"></a>Omówienie rozwiązań

Rozwiązanie to grupowanie jednego lub więcej projektów, które współpracują ze sobą w celu utworzenia aplikacji. Informacje o projekcie i stanie dotyczące rozwiązania są przechowywane w dwóch różnych plikach rozwiązania. [Plik rozwiązania (.sln)](solution-dot-sln-file.md) jest oparty na tekście i może być umieszczony pod kontrolą kodu źródłowego i współużytkowany przez użytkowników. Opcja [użytkownika rozwiązania (.suo) plik](solution-user-options-dot-suo-file.md) jest binarny. W rezultacie plik .suo nie może być umieszczony pod kontrolą kodu źródłowego i zawiera informacje specyficzne dla użytkownika.

Każdy VSPackage można zapisać do dowolnego typu pliku rozwiązania. Ze względu na charakter plików istnieją dwa różne interfejsy zaimplementowane do pisania do nich. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> zapisuje informacje tekstowe do pliku .sln, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> a interfejs zapisuje strumienie binarne do pliku .suo.

> [!NOTE]
> Projekt nie musi jawnie zapisywać wpis dla siebie w pliku rozwiązania; środowisko obsługuje to dla projektu. W związku z tym, chyba że chcesz dodać dodatkową zawartość specjalnie do pliku rozwiązania, nie trzeba rejestrować VSPackage w ten sposób.

Każdy VSPackage obsługi trwałości rozwiązania używa trzech <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejsów, interfejs, który jest implementowany przez środowisko `IVsPersistSolutionProps` `IVsPersistSolutionOpts`i wywoływane przez VSPackage i , które są zaimplementowane przez VSPackage. Interfejs `IVsPersistSolutionOpts` musi być zaimplementowany tylko wtedy, gdy prywatne informacje mają być zapisywane przez VSPackage do pliku .suo.

Po otwarciu rozwiązania odbywa się następujący proces.

1. Środowisko odczytuje rozwiązanie.

2. Jeśli środowisko znajdzie `CLSID`, ładuje odpowiednie VSPackage.

3. Jeśli VSPackage jest ładowany, środowisko wywołuje `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejs dla interfejsu, który wymaga VSPackage.

   - Podczas odczytywania z pliku .sln środowisko wymaga `QueryInterface` `IVsPersistSolutionProps`.

   - Podczas odczytywania z pliku .suo środowisko wymaga `QueryInterface` `IVsPersistSolutionOpts`.

   Szczegółowe informacje dotyczące korzystania z tych plików można znaleźć w [Rozwiązaniu (. Sln) Opcje](../../extensibility/internals/solution-dot-sln-file.md) użytkownika plików i [rozwiązań (. Suo) Plik](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Jeśli chcesz utworzyć nową konfigurację rozwiązania składającą się z dwóch konfiguracji projektów i wykluczającą jedną trzecią z kompilacji, musisz użyć interfejsu użytkownika stron właściwości lub automatyzacji. Nie można zmienić konfiguracji menedżera kompilacji rozwiązania i ich właściwości bezpośrednio, ale można `SolutionBuild` manipulować menedżera kompilacji rozwiązania przy użyciu klasy z DTE w modelu automatyzacji. Aby uzyskać więcej informacji na temat konfigurowania rozwiązań, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
