---
title: Tworzenie rozszerzenia za pomocą okna narzędzia | Dokumentacja firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2741a7f9d27c303981ed4b179e3fe3d7cd63f020
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194152"
---
# <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia za pomocą okna narzędzi

W tej procedurze opisano sposób użyć szablonu projektu VSIX i **okna narzędzi niestandardowych** szablonu elementu Tworzenie rozszerzenia za pomocą okna narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne

 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Utworzenie okna narzędzia

1. Utwórz projekt VSIX, o nazwie **FirstWindow**. Można znaleźć szablonu projektu VSIX w **nowy projekt** okna dialogowego, wyszukując pozycję "vsix".

2. Po otwarciu projektu, należy dodać szablon elementu okno narzędzia o nazwie **MyWindow**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C#** > **rozszerzalności** i wybierz **okna narzędzi niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku okna narzędzi, aby *MyWindow.cs*.

3. Skompiluj projekt, a następnie rozpocząć debugowanie.

   Pojawi się doświadczalnym wystąpieniu programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).

4. W doświadczalnym wystąpieniu, przejdź do **widoku** > **inne Windows**.

   Powinien zostać wyświetlony element menu dla **MyWindow**. Kliknij go.

   Powinien zostać wyświetlony okna narzędzi z tytułem **MyWindow** i powiedzenie przycisk **kliknij mnie!.**