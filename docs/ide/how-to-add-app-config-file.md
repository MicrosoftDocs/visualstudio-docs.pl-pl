---
title: Jak dodać plik app.config do projektu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593645"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Jak: Dodawanie pliku konfiguracji aplikacji do projektu języka C#

Dodając plik konfiguracji aplikacji (plik*app.config)* do projektu języka C#, można dostosować sposób, w jaki środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji na temat plików konfiguracyjnych aplikacji, zobacz [Jak środowisko wykonawcze lokalizuje zestawy (.NET Framework).](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)

> [!NOTE]
> Aplikacje platformy uniwersalnej systemu Windows nie zawierają pliku *app.config.*

Podczas tworzenia projektu środowisko programistyczne automatycznie kopiuje plik *app.config,* zmienia nazwę pliku kopii, aby dopasować go do pliku wykonywalnego, a następnie przenosi kopię do katalogu **bin.**

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu języka C#

1. Na pasku menu wybierz pozycję **Project** > **Add New Item**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

1. Rozwiń rozwiń **pozycję Zainstalowane** > **elementy języka Visual C#,** a następnie wybierz szablon **pliku konfiguracji aplikacji.**

1. W polu tekstowym **Nazwa** wprowadź nazwę, a następnie wybierz przycisk **Dodaj.**

     Plik o nazwie *app.config* zostanie dodany do projektu.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schemat pliku konfiguracyjnego (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)
