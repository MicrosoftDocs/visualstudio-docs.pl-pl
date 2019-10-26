---
title: Dodawanie usługi Azure Storage przy użyciu usług połączonych | Microsoft Docs
description: Dodawanie usługi Azure Storage do aplikacji przy użyciu okna dialogowego Dodawanie usług połączonych programu Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: ca65086ce7ce09a1ca288c2f5cd04c31e00f8e95
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911897"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Dodawanie usługi Azure Storage przy użyciu usług połączonych programu Visual Studio

Za pomocą programu Visual Studio można połączyć dowolne z następujących elementów w usłudze Azure Storage przy użyciu okna dialogowego **Dodawanie połączonych usług** :

- C#Usługa w chmurze
- Usługa mobilna zaplecza platformy .NET
- ASP.NET witryna sieci Web lub usługa
- Usługa ASP.NET Core
- Usługa zadań WebJob platformy Azure

Funkcja połączonej usługi dodaje wszystkie konieczne odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracyjne.

Po zakończeniu okno dialogowe **Dodawanie połączonych usług** automatycznie wyświetli dokumentację opisującą kroki wymagane do rozpoczęcia pracy z magazynem obiektów blob, kolejkami i tabelami.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [usługi połączone w programie Visual Studio dla komputerów Mac](/visualstudio/mac/connected-services).

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Nawiązywanie połączenia z usługą Azure Storage przy użyciu okna dialogowego połączone usługi

1. Otwieranie projektu w programie Visual Studio

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **usługi połączone** , a następnie z menu kontekstowego wybierz polecenie **Dodaj podłączoną usługę**.

    ![Dodawanie usługi połączonej z platformą Azure](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Na stronie **usługi połączone** wybierz pozycję **Magazyn w chmurze z usługą Azure Storage**.

    ![Dodawanie usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. W oknie dialogowym **Azure Storage** Wybierz istniejące konto magazynu i wybierz pozycję **Dodaj**.

    Jeśli musisz utworzyć konto magazynu, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto magazynu do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Aby utworzyć konto magazynu:

   1. Wybierz pozycję **Utwórz nowe konto magazynu** w dolnej części okna dialogowego.

   1. Wypełnij okno dialogowe **Tworzenie konta magazynu** , a następnie wybierz pozycję **Utwórz**.

       ![Nowe konto usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po wyświetleniu okna dialogowego **usługi Azure Storage** nowe konto magazynu zostanie wyświetlone na liście. Wybierz nowe konto magazynu z listy, a następnie wybierz pozycję **Dodaj**.

1. Usługa połączona do magazynu jest wyświetlana w węźle **odwołania do usługi** projektu.

## <a name="how-your-project-is-modified"></a>Jak projekt jest modyfikowany

Po zakończeniu okna dialogowego program Visual Studio dodaje odwołania i modyfikuje niektóre pliki konfiguracji. Określone zmiany są zależne od typu projektu:

- Projekt ASP.NET — [co się stało — projekty ASP.NET](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs)
- ASP.NET Core Project — [co się stało — projekty ASP.NET 5](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs)
- Projekt usługi w chmurze (role sieci Web i proces roboczy) — [co się stało — projekty usług w chmurze](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs)
- Projekt Zadania WebJob — [co się stało z projektami zadań WebJob](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="see-also"></a>Zobacz także

- [Forum MSDN: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog zespołu Microsoft Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Dokumentacja usługi Azure Storage](/azure/storage/)
- [Połączone usługi (Visual Studio dla komputerów Mac)](/visualstudio/mac/connected-services)
