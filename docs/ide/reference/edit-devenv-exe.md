---
title: -Edit (devenv.exe)
description: Dowiedz się, jak otworzyć określony plik w istniejącym wystąpieniu programu Visual Studio za pomocą przełącznika wiersza polecenia Edit devenv.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45d0b1342ea0e53c4897881ebb5cfee0a7241d6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882078"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otwiera określony plik w istniejącym wystąpieniu programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *File1*

  Opcjonalny. Plik do otwarcia w istniejącym wystąpieniu programu Visual Studio. Jeśli wystąpienie programu Visual Studio nie istnieje, nowe wystąpienie jest tworzone z uproszczonym układem okna, a narzędzie otwiera *plik1* w nowym wystąpieniu.

- *Plikn*

  Opcjonalny. Co najmniej jeden dodatkowy plik do otwarcia w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Gdy nie określono pliku, istniejące wystąpienie programu Visual Studio otrzymuje fokus. Jeśli plik nie zostanie określony i żadne wystąpienie programu Visual Studio nie istnieje, narzędzie tworzy wystąpienie z uproszczonym układem okna.

Jeśli istniejące wystąpienie programu Visual Studio jest w stanie modalnym, plik zostanie otwarty w istniejącym wystąpieniu, gdy program Visual Studio zakończy stan modalny. Na przykład taka sytuacja może wystąpić, gdy okno [dialogowe Opcje](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarte.

Jeśli jest otwarte więcej niż jedno wystąpienie programu Visual Studio, plik zostanie otwarty w ostatnio otwartym wystąpieniu.

## <a name="example"></a>Przykład

Pierwszy przykład otwiera plik `MyFile.cs` w istniejącym wystąpieniu programu Visual Studio. Jeśli wystąpienie programu Visual Studio nie istnieje, narzędzie otwiera plik w nowym wystąpieniu. Drugi przykład jest podobny, z tą różnicą, że otwiera trzy pliki zamiast tylko jednego pliku.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
