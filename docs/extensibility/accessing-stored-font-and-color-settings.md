---
title: Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c270c67d21c023310df5b25c015afa754787a33f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093559"
---
# <a name="access-stored-font-and-color-settings"></a>Dostęp przechowywane ustawienia czcionek i kolorów

Visual Studio, które są przechowywane w zintegrowanym środowisku programistycznym (IDE), zmodyfikować ustawienia czcionek i kolorów w rejestrze. Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu uzyskać dostępu do tych ustawień.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Aby zainicjować utrwalanie stanu czcionek i kolorów

Informacje o czcionek i kolorów są przechowywane według kategorii w następującej lokalizacji rejestru: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], gdzie  *\<CategoryGUID >* to kategoria identyfikatora GUID.

W związku z tym aby zainicjować trwałości, pakietu VSPackage musi:

- Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu, wywołując `QueryService` względem dostawcy usługi global service.

     `QueryService` musi zostać wywołana przy użyciu argumentu identyfikator usługi z `SID_SVsFontAndColorStorage` i argument identyfikator interfejsu `IID_IVsFontAndColorStorage`.

- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodę, aby otworzyć kategorii w celu jego utrwalenia przy użyciu identyfikatora GUID danej kategorii i flagi trybu jako argumenty.

     Tryb, określony przez `fFlags` argument, jest tworzony z wartości w <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> wyliczenia. W tym trybie kontrolki:

    - Ustawienia, które mogą być udostępniane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

    - Wszystkie ustawienia lub tylko te ustawienia, które zmodyfikować użytkowników i które można odzyskać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

    - Sposób propagowanie zmian ustawień użytkownika.

    - Format wartości kolorów, które są używane.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Aby użyć utrwalanie stanu czcionek i kolorów

Utrwalanie czcionki i kolory obejmuje:

- Synchronizacja ustawień środowiska IDE, za pomocą ustawień przechowywanych w rejestrze.

- Propagowanie informacji modyfikacji rejestru.

- Ustawianie i pobieranie ustawień przechowywanych w rejestrze.

Synchronizacja ustawień magazynu z ustawieniami środowiska IDE jest dużej mierze przejrzyste. Podstawowy IDE automatycznie zapisuje zaktualizowanych ustawień dla **Wyświetle elementy** wpisów rejestru kategorii.

Jeśli wiele pakietów VSPackage mają określoną kategorię, pakietu VSPackage powinny wymagać generowane są zdarzenia podczas metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu służą do modyfikowania ustawień rejestru przechowywanych.

Generowanie zdarzeń nie jest włączona domyślnie. Aby włączyć generowanie zdarzeń, kategorii muszą być otwarte przy użyciu [__FCSTORAGEFLAGS. FCSF_PROPAGATECHANGES](<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS.FCSF_PROPAGATECHANGES>). Otwieranie kategorii powoduje, że środowisko IDE do wywołania odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metody, która implementuje pakietu VSPackage.

> [!NOTE]
> Modyfikacje za pośrednictwem **czcionek i kolorów** stronie właściwości generowanie zdarzeń niezależnie od <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu, aby ustalić, czy aktualizację pamięci podręcznej ustawienia czcionek i kolorów jest wymagana przed wywołaniem metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> klasy.

### <a name="store-and-retrieve-information"></a>Store i pobieranie informacji

Uzyskać lub skonfigurować informacje, które użytkownik może modyfikować dla nazwanego wyświetlanego elementu w kategorii otwarte, wywołaj pakietów VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody.

Informacje o czcionki atrybuty dla określonej kategorii są uzyskiwane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metody.

> [!NOTE]
> `fFlags` Argument, który jest przekazywany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metody w momencie otwarcia tej kategorii definiuje zachowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody. Domyślnie te metody zwracają tylko informacje na temat wyświetlania elementów, które uległy zmianie. Jednak jeśli kategoria jest otwarty za pomocą [__FCSTORAGEFLAGS. FCSF_LOADDEFAULTS](<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS.FCSF_LOADDEFAULTS>) Flaga zarówno zaktualizowane i Wyświetl niezmienione elementy może zostać oceniony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

Domyślnie tylko zmienione **Wyświetle elementy** informacje są przechowywane w rejestrze. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Interfejsu nie może służyć do pobierania wszystkich ustawień czcionek i kolorów.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody zwracają REGDB_E_KEYMISSING, (0x80040152L) możesz użyć do pobrania informacji o zmianie **Wyświetle elementy**.

Ustawienia wszystkich **Wyświetle elementy** w szczególności **kategorii** można uzyskać za pomocą metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implementowanie niestandardowych kategorii i wyświetlania elementów](../extensibility/implementing-custom-categories-and-display-items.md)