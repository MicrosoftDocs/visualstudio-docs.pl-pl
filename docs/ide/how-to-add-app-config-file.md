---
title: Jak dodać plik app.config do projektu
description: Dowiedz się, jak dodać plik app.config do projektu C#, aby dostosować sposób lokalizowania i ładowania plików zestawu przez środowisko uruchomieniowe języka wspólnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e9280451d7841755cb3085726843bf6fc1443f8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948286"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Instrukcje: Dodawanie pliku konfiguracji aplikacji do projektu C#

Dodając plik konfiguracji aplikacji (plik *app.config* ) do projektu C#, można dostosować sposób lokalizowania i ładowania plików zestawu przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji na temat plików konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacje platformy UWP nie zawierają pliku *app.config* .

Podczas kompilowania projektu środowisko programistyczne automatycznie kopiuje plik *app.config* , zmienia nazwę pliku kopii w celu dopasowania do pliku wykonywalnego, a następnie przenosi kopię do katalogu **bin** .

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

1. Rozwiń węzeł **zainstalowane**  >  **elementy Visual C#**, a następnie wybierz szablon **plik konfiguracji aplikacji** .

1. W polu tekstowym **Nazwa** wprowadź nazwę, a następnie wybierz przycisk **Dodaj** .

     Plik o nazwie *app.config* jest dodawany do projektu.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)
