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
ms.openlocfilehash: e68f7503ecc75c03e9f4beda2003415d3175ee7e
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954472"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Dodawanie usługi Azure storage przy użyciu programu Visual Studio podłączone usługi
Za pomocą programu Visual Studio, można nawiązać żadnego z następujących usługi Azure Storage za pomocą **Dodaj usługi połączone** okno dialogowe:

- Usługa w chmurze języka C#
- Usługi mobilnej zaplecza platformy .NET
- Witryny sieci Web ASP.NET lub usługi
- Usługi ASP.NET Core
- Usługa zadań WebJob platformy Azure

Funkcje usługi połączonej dodaje wymagane odwołania i kod połączenia do projektu i odpowiednio modyfikuje pliki konfiguracji.

Po zakończeniu **Dodaj usługi połączone** okna dialogowego automatycznie wyświetla dokumentacji szczegółowych informacji na temat kroków wymaganych do rozpoczęcia pracy z magazynem obiektów blob, kolejek i tabel.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Łączenie się z magazynem platformy Azure za pomocą okna dialogowego podłączone usługi
1. Otwórz projekt w programie Visual Studio

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **podłączone usługi** węzeł i z menu kontekstowe i wybierz **Dodaj podłączoną usługę**.

    ![Dodaj Azure usługa połączona](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. W **podłączone usługi** wybierz opcję **magazynu w chmurze z usługą Azure Storage**.

    ![Dodawanie usługi Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. W **usługi Azure Storage** okno dialogowe, wybierz istniejące konto magazynu i wybierz **Dodaj**.

    Jeśli musisz utworzyć konto magazynu, przejdź do następnego kroku. W przeciwnym razie przejdź do kroku 6.

    ![Dodaj istniejące konto magazynu do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Aby utworzyć konto magazynu:

   1. Wybierz **Utwórz nowe konto magazynu** w dolnej części okna dialogowego.

   1. Wypełnij **Utwórz konto magazynu** okna dialogowego, a następnie wybierz **Utwórz**.

       ![Nowe konto usługi Azure storage](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Gdy **usługi Azure Storage** zostanie wyświetlone okno dialogowe, nowe konto magazynu jest wyświetlana na liście. Wybierz nowe konto magazynu na liście, a następnie wybierz pozycję **Dodaj**.

1. Magazyn usługi połączonej jest wyświetlany w obszarze **odwołania do usług** węzła projektu.

## <a name="how-your-project-is-modified"></a>Jak jest modyfikowana projektu
Po zakończeniu okna dialogowego programu Visual Studio dodaje odwołania i modyfikuje niektórych plików konfiguracyjnych. Konkretne zmiany są zależne od typu projektu:

- Projekt platformy ASP.NET — [co się stało — projektów platformy ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- Projekt platformy ASP.NET Core — [co się stało — projektów programu ASP.NET 5](http://go.microsoft.com/fwlink/p/?LinkId=513124)
- Projekt usługi w chmurze (role sieć web i ról procesów roboczych) - [co się stało — projektów usług w chmurze](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- Projekt zadania WebJob — [co się stało — projekty zadań WebJob](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Następne kroki
- [MSDN Forum: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog zespołu usługi Microsoft Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/)
- [Dokumentacja usługi Azure Storage](https://docs.microsoft.com/azure/storage/)
