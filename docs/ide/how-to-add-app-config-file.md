---
title: Jak dodać pliku app.config do projektu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3eb813dc5d4389b002851a904d61219b0d5c316e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593645"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do C# projektu

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
