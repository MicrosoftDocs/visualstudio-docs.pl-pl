---
title: Jak dodać plik App. config do projektu
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654263"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Instrukcje: Dodawanie pliku konfiguracji aplikacji do C# projektu

Dodając plik konfiguracji aplikacji (plik*App. config* ) do C# projektu, można dostosować sposób lokalizowania i ładowania plików zestawu przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji na temat plików konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacje platformy UWP nie zawierają pliku *App. config* .

Podczas kompilowania projektu środowisko programistyczne automatycznie kopiuje plik *App. config* , zmienia nazwę pliku kopii w celu dopasowania do pliku wykonywalnego, a następnie przenosi kopię do katalogu **bin** .

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do C# projektu

1. Na pasku menu wybierz **projekt**  > **Dodaj nowy element**.

     Pojawi się okno dialogowe **Dodaj nowy element** .

1. Rozwiń węzeł **zainstalowane**  > **elementy wizualne C#** , a następnie wybierz szablon **plik konfiguracji aplikacji** .

1. W polu tekstowym **Nazwa** wprowadź nazwę, a następnie wybierz przycisk **Dodaj** .

     Plik o nazwie *App. config* jest dodawany do projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)