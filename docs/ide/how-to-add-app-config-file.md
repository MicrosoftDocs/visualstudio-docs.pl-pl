---
title: Jak dodać plik app.config do projektu
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe659979cadf4d9e5752f7bbe85150aae848de08
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770830"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Instrukcje: Dodawanie pliku konfiguracji aplikacji do projektu C#

Dodając plik konfiguracji aplikacji (plik*app.config* ) do projektu C#, można dostosować sposób lokalizowania i ładowania plików zestawu przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji na temat plików konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacje platformy UWP nie zawierają pliku *app.config* .

Podczas kompilowania projektu środowisko programistyczne automatycznie kopiuje plik *app.config* , zmienia nazwę pliku kopii w celu dopasowania do pliku wykonywalnego, a następnie przenosi kopię do katalogu **bin** .

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

1. Rozwiń węzeł **zainstalowane**  >  **elementy Visual C#**, a następnie wybierz szablon **plik konfiguracji aplikacji** .

1. W polu tekstowym **Nazwa** wprowadź nazwę, a następnie wybierz przycisk **Dodaj** .

     Plik o nazwie *app.config* jest dodawany do projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)
