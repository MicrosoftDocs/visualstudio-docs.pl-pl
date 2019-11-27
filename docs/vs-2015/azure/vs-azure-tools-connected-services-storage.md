---
title: Dodawanie usługi Azure Storage przy użyciu usług połączonych
description: Dodawanie usługi Azure Storage do swojej aplikacji za pomocą okna dialogowego programu Visual Studio Dodaj połączone usługi
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 6d7bf7901ab33dc6dba50013ebdfa05c3188cd6c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300170"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Dodawanie usługi Azure storage przy użyciu programu Visual Studio podłączone usługi
Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure Storage przy użyciu okna dialogowego **Dodawanie połączonych usług** :

- Usługa w chmurze języka C#
- Usługi mobilnej zaplecza platformy .NET
- Witryny sieci Web ASP.NET lub usługi
- Usługi ASP.NET Core
- Usługa zadań WebJob platformy Azure

Funkcje usługi połączonej dodaje wymagane odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracji.

Po zakończeniu okno dialogowe **Dodawanie połączonych usług** automatycznie wyświetli dokumentację opisującą kroki wymagane do rozpoczęcia pracy z magazynem obiektów blob, kolejkami i tabelami.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Łączenie się z magazynem platformy Azure za pomocą okna dialogowego podłączone usługi
1. Otwórz projekt w programie Visual Studio

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

    ![Dodaj Azure usługa połączona](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Na stronie **usługi połączone** wybierz pozycję **Magazyn w chmurze z usługą Azure Storage**.

    ![Dodawanie usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. W oknie dialogowym **Azure Storage** Wybierz istniejące konto magazynu i wybierz pozycję **Dodaj**.

    Jeśli musisz utworzyć konto magazynu, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto magazynu do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Aby utworzyć konto magazynu:

   1. Wybierz pozycję **Utwórz nowe konto magazynu** w dolnej części okna dialogowego.

   1. Wypełnij okno dialogowe **Tworzenie konta magazynu** , a następnie wybierz pozycję **Utwórz**.

       ![Nowe konto usługi Azure storage](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po wyświetleniu okna dialogowego **usługi Azure Storage** nowe konto magazynu zostanie wyświetlone na liście. Wybierz nowe konto magazynu z listy, a następnie wybierz pozycję **Dodaj**.

1. Usługa połączona do magazynu jest wyświetlana w węźle **odwołania do usługi** projektu.

## <a name="how-your-project-is-modified"></a>Jak jest modyfikowana projektu
Po zakończeniu okna dialogowego programu Visual Studio dodaje odwołania i modyfikuje niektórych plików konfiguracyjnych. Konkretne zmiany są zależne od typu projektu:

- Projekt ASP.NET — [co się stało — projekty ASP.NET](https://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core Project — [co się stało — projekty ASP.NET 5](https://go.microsoft.com/fwlink/p/?LinkId=513124)
- Projekt usługi w chmurze (role sieci Web i proces roboczy) — [co się stało — projekty usług w chmurze](https://go.microsoft.com/fwlink/p/?LinkId=516965)
- Projekt Zadania WebJob — [co się stało z projektami zadań WebJob](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Kolejne kroki
- [Forum MSDN: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog zespołu Microsoft Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Dokumentacja usługi Azure Storage](https://docs.microsoft.com/azure/storage/)
