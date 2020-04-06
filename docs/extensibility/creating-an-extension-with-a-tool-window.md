---
title: Tworzenie rozszerzenia za pomocą okna narzędzia | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739541"
---
# <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzia

W tej procedurze dowiesz się, jak użyć szablonu projektu VSIX i szablonu elementu **okno narzędzia niestandardowego,** aby utworzyć rozszerzenie z oknem narzędzia.

## <a name="prerequisites"></a>Wymagania wstępne

 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Tworzenie okna narzędzia

1. Utwórz projekt VSIX o nazwie **FirstWindow**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Po otwarciu projektu dodaj szablon elementu okna narzędzia o nazwie **MyWindow**. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz pozycję **Okno narzędzia niestandardowego**. W polu **Nazwa** u dołu okna zmień nazwę pliku okna narzędzia na *MyWindow.cs*.

3. Skompiluj projekt i rozpocznij debugowanie.

   Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

4. W przypadku eksperymentalnego przejdź do **strony Wyświetl** > **inne systemy Windows**.

   Powinien zostać wyświetlony element menu dla **mywindow**. Kliknij go.

   Powinno zostać wyświetlene okno narzędzia z tytułem **MyWindow** i przyciskiem **"Kliknij mnie!".**
