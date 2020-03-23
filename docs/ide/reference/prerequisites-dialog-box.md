---
title: Wstępnie wymagane składniki — Okno dialogowe
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ecbba1a1c5e8670fd9adcafdfed8cec21dd3912
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567908"
---
# <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe

Okno dialogowe **Wymagania wstępne** określa, które składniki wymagań wstępnych są zainstalowane, jak są instalowane i jaka kolejność pakietów jest instalowana.

![Okno dialogowe Wymagania wstępne w programie Visual Studio](media/prerequisites-dialog-box.png)

Aby uzyskać dostęp do okna dialogowego, wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie wybierz pozycję**Właściwości** **projektu** > . Po wyświetleniu **projektanta projektu** wybierz kartę **Publikuj,** a następnie wybierz pozycję **Wymagania wstępne**. W przypadku projektów instalatora w menu **Projekt** kliknij polecenie **Właściwości**. Po **wyświetleniu** okna dialogowego Strony właściwości kliknij pozycję **Wymagania wstępne**.

## <a name="uielement-list"></a>Lista UIElement

|Element|Opis|
|-------------|-----------------|
|**Tworzenie programu instalacyjnego do instalowania składników wstępnych**|Zawiera składniki wymaganego w programie instalacyjnym aplikacji *(Setup.exe),* dzięki czemu zostaną zainstalowane przed aplikacją w kolejności zależności. Ta opcja jest wybrana domyślnie. Jeśli nie jest zaznaczona, nie jest tworzony *plik Setup.exe.*|
|**Wybierz wymagania wstępne do zainstalowania**|Określa, czy mają być instalowane składniki, takie jak .NET Framework i biblioteki wykonawcze języka C++.<br /><br />Na przykład zaznaczając pole wyboru obok **programu SQL Server 2012 Express,** należy określić, że program instalacyjny musi sprawdzić, czy ten składnik jest zainstalowany na komputerze docelowym, i zainstalować go, jeśli nie jest.<br /><br />Aby uzyskać szczegółowe informacje o każdym pakiecie wymagań wstępnych, zobacz [Informacje o wymaganiach wstępnych](#prerequisites-information).|
|**Pobieranie wymagań wstępnych ze strony internetowej dostawcy komponentu**|Określa, że składniki wymaganego są instalowane w witrynie sieci Web dostawcy. Jest to domyślne ustawienie opcji.|
|**Pobieranie wymagań wstępnych z tej samej lokalizacji co moja aplikacja**|Określa, że składniki wymaganego być zainstalowane z tej samej lokalizacji co aplikacja. Spowoduje to skopiowanie wszystkich pakietów wymaganych do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
|**Pobieranie wymagań wstępnych z następującej lokalizacji**|Określa, że składniki wymaganego są instalowane z wprowadzonej lokalizacji. Za pomocą przycisku **Przeglądaj** można wybrać lokalizację.|

> [!NOTE]
> Aby uzyskać informacje o tym, gdzie umieścić wymagania wstępne, zobacz [Tworzenie pakietów inicjującego](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informacje o wymaganiach wstępnych

Składniki wymagań wstępnych, które pojawiają się w oknie dialogowym **Wymagania wstępne** mogą różnić się od tych na poniższej liście. Pakiety wymagań wstępnych wymienione w **oknie dialogowym Wymagania wstępne** są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli następnie zmienisz platformę docelową projektu, musisz ręcznie wybrać wymagania wstępne, aby dopasować się do nowej struktury docelowej.

|Element|Opis|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Ten pakiet instaluje następujące elementy:<br /><br /> - .NET Framework wersje 2.0, 3.0 i 3.5.<br />- Obsługa wszystkich wersji programu .NET Framework w systemach operacyjnych 32-bitowych (x86) i 64-bitowych (x64).<br />- Pakiety językowe dla każdej wersji programu .NET Framework, która jest zainstalowana z pakietem.<br />- Dodatki Service Pack dla platformy .NET Framework 2.0 i 3.0.<br /><br /> Program .NET Framework 3.0 jest dołączony do systemu Windows Vista, a program .NET Framework 3.5 jest dołączony do programu Visual Studio. Program .NET Framework 3.5 jest wymagany dla wszystkich projektów języka Visual Basic i C#, które są kompilowane dla 32-bitowych systemów operacyjnych i dla których struktura docelowa jest ustawiona na **.NET Framework 3.5**oraz dla projektów języka Visual Basic i C# skompilowanych dla 64-bitowych systemów operacyjnych. (IA64 nie jest obsługiwany.) Należy zauważyć, że projekty języka Visual Basic i C# są domyślnie kompilowane dla dowolnej architektury procesora CPU. Aby uzyskać więcej informacji, zobacz [Omówienie kierowania na platformę](../../ide/visual-studio-multi-targeting-overview.md) i [wdrażanie wymagań wstępnych dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Ten pakiet instaluje .NET Framework 4.x dla platform x86 i x64.|
|**Typy CLR systemu Microsoft dla programu SQL Server 2014 (x64 i x86)**|Ten pakiet instaluje typy CLR systemu Microsoft Dla programu SQL Server 2014 dla x64 lub x86.|
|**SQL Server 2008 R2 Express**|Ten pakiet instaluje program Microsoft SQL Server 2008 R2 Express, bezpłatną wersję programu Microsoft SQL Server 2008 R2, idealną bazę danych dla małych aplikacji sieci Web, serwerów lub komputerów stacjonarnych. Może być używany za darmo do rozwoju i produkcji.|
|**SQL Server 2012 Express**|Ten pakiet instaluje program Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ten pakiet instaluje usługę Microsoft SQL Server 2012 Express LocalDB.|
|**Biblioteki środowiska wykonawczego visual C++ "14" (ARM)**|Ten pakiet instaluje biblioteki w czasie wykonywania języka Visual C++ dla architektury Itanium, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programowania, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Biblioteki środowiska wykonawczego Visual C++ "14" (x64)**|Ten pakiet instaluje biblioteki w czasie wykonywania języka Visual C++ dla systemów operacyjnych x64, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programowania, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Biblioteki środowiska wykonawczego Visual C++ "14" (x86)**|Ten pakiet instaluje biblioteki w czasie wykonywania języka Visual C++ dla systemów operacyjnych x86, które zapewniają procedury programowania dla systemu operacyjnego Microsoft Windows. Te procedury automatyzują wiele typowych zadań programowania, które nie są dostarczane przez języki C i C++.<br /><br /> Aby uzyskać więcej informacji, zobacz [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Zobacz też

- [Strona publikowania, Projektant projektu](../../ide/reference/publish-page-project-designer.md)
- [Wymagania wstępne wdrażania aplikacji](../../deployment/application-deployment-prerequisites.md)
- [Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Omówienie kierowania na ramy](../../ide/visual-studio-multi-targeting-overview.md)
