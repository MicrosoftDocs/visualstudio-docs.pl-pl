---
title: Uruchamianie i debugowanie usługi w chmurze platformy Azure na komputerze lokalnym za pomocą emulatora Express | Microsoft Docs
description: Używanie emulatora Express do uruchamiania i debugowania usługi w chmurze na komputerze lokalnym
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d89762511e88e296a51c781c6a403c2dd227ed4f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293254"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uruchamianie i debugowanie usługi w chmurze platformy Azure na maszynie lokalnej za pomocą emulatora w wersji Express
Za pomocą emulatora Express można testować i debugować usługę w chmurze bez uruchamiania programu Visual Studio jako administrator. Ustawienia projektu można ustawić tak, aby używały emulatora Express lub pełnego emulatora, w zależności od wymagań usługi w chmurze. Aby uzyskać więcej informacji na temat pełnego emulatora, zobacz [Uruchamianie aplikacji platformy Azure w emulatorze obliczeniowym](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Korzystanie z emulatora Express w programie Visual Studio
Podczas tworzenia projektu platformy Azure w zestawie Azure SDK 2,3 lub nowszym jest używany automatycznie emulator Express. W przypadku istniejących projektów utworzonych przy użyciu wcześniejszej wersji zestawu Azure SDK wykonaj następujące kroki, aby wybrać emulator Express:

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Właściwości**.

1. Na stronie właściwości projektu wybierz kartę **Sieć Web** .

    ![Właściwości projektu usługi w chmurze platformy Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. W obszarze **lokalny serwer programistyczny**wybierz opcję **Użyj IIS Express**.

1. W obszarze **emulator**wybierz pozycję **Użyj emulator Express**.
   
1. Aby uruchomić emulator Express, uruchom następujące polecenie w wierszu polecenia: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Ograniczenia emulatora Express
Następujące problemy są znanymi ograniczeniami emulatora Express: 

- Emulator Express nie jest zgodny z serwerem sieci Web usług IIS.
- Usługa w chmurze może zawierać wiele ról, ale każda rola jest ograniczona do jednego wystąpienia.
- Nie można uzyskać dostępu do numerów portów poniżej 1000. Jeśli używasz dostawcy uwierzytelniania, który zwykle korzysta z portu poniżej 1000, może zajść potrzeba zmiany tej wartości na numer portu, który znajduje się powyżej 1000.
- Wszelkie ograniczenia dotyczące emulatora obliczeń platformy Azure mają zastosowanie również do emulatora Express. Na przykład nie można mieć więcej niż 50 wystąpień ról na wdrożenie. Aby uzyskać więcej informacji na temat emulatora obliczeń platformy Azure, zobacz [Uruchamianie aplikacji platformy Azure w emulatorze obliczeniowym](https://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Kolejne kroki
[Debugowanie usług Azure Cloud Services](vs-azure-tools-debugging-cloud-services-overview.md)
