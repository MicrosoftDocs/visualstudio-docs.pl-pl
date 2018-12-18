---
title: Za pomocą Emulator Express uruchamianie i debugowanie usługi w chmurze platformy Azure na maszynie lokalnej | Dokumentacja firmy Microsoft
description: Za pomocą Emulator Express uruchamianie i debugowanie usługi w chmurze na komputerze lokalnym
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003298"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uruchamianie i debugowanie usługi w chmurze platformy Azure na maszynie lokalnej za pomocą emulatora w wersji Express
Za pomocą Emulator Express, można przetestować i debugowanie usługi w chmurze bez konieczności uruchamiania programu Visual Studio jako administrator. Możesz ustawić ustawienia projektu, aby użyć Emulator Express lub pełnego emulatora, w zależności od wymagań usługi w chmurze. Aby uzyskać więcej informacji na temat pełnego emulatora, zobacz [uruchamiania aplikacji platformy Azure w emulatorze obliczeń](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Za pomocą Emulator Express w programie Visual Studio
Podczas tworzenia projektu platformy Azure w systemie Azure SDK 2.3 lub nowszym, Emulator Express automatycznie jest używana. W przypadku istniejących projektów, które zostały utworzone we wcześniejszej wersji zestawu SDK platformy Azure wykonaj następujące kroki, aby wybrać Emulator Express:

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **właściwości**.

1. Na stronach właściwości projektów, wybierz **Web** kartę.

    ![Właściwości projektu usługi w chmurze platformy Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. W obszarze **lokalnego serwera wdrożeniowego**, wybierz opcję **opcję Użyj usług IIS Express**.

1. W obszarze **emulatora**, wybierz opcję **Użyj Emulator Express**.
   
1. Aby uruchomić Emulator Express, uruchom następujące polecenie w wierszu polecenia: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express ograniczenia
Znane ograniczenia Emulator Express następujące problemy: 

- Emulator Express nie jest zgodna z serwerem sieci Web usług IIS.
- Usługi w chmurze może zawierać wiele ról, ale każda rola jest ograniczona do jednego wystąpienia.
- Nie masz dostępu do numerów portów poniżej 1000. Jeśli używasz dostawcy uwierzytelniania, który zwykle używa portu poniżej 1000, może być konieczne Zmień tę wartość na numer portu, który jest ponad 1000.
- Wszelkie ograniczenia, które są stosowane do emulatora obliczeń platformy Azure dotyczą również Emulator Express. Na przykład nie może mieć więcej niż 50 wystąpień roli na wdrożenie. Aby uzyskać więcej informacji o emulatorze obliczeń systemu Azure, zobacz [uruchamiania aplikacji platformy Azure w emulatorze obliczeń](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Następne kroki
[Debugowanie usług Azure cloud services](https://msdn.microsoft.com/library/azure/ee405479.aspx)
