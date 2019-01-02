---
title: Jak dodać pliku app.config do projektu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 11bc55316414298cf61a27854182f4831feb1ded
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910103"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Instrukcje: Dodawanie pliku konfiguracji aplikacji do C# projektu

Przez dodanie pliku konfiguracji aplikacji (*app.config* plików) do C# projektu, można dostosować, jak środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacje platformy uniwersalnej systemu Windows nie zawierają *app.config* pliku.

Podczas tworzenia projektu środowiska programistycznego automatycznie kopiuje swoje *app.config* plik, zmienia nazwę pliku kopiowania, aby dopasować plik wykonywalny i przenosi kopię **bin** katalog.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do C# projektu

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

1. Rozwiń **zainstalowane** > **Visual C# elementów**, a następnie wybierz **pliku konfiguracji aplikacji** szablonu.

1. W **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.

     Plik o nazwie *app.config* zostanie dodany do projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)