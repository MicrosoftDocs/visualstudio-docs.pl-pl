---
title: Tworzenie wystąpień projektu przy użyciu fabryk projektów | Microsoft Docs
description: Dowiedz się, jak utworzyć wystąpienia klasy projektu za pomocą fabryk projektów w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b7c3fbe5b5b7fd59fe0e57376290181f3e9a20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056805"
---
# <a name="create-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektu przy użyciu fabryk projektów
Typy projektów w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykorzystują *fabrykę projektu* do tworzenia wystąpień obiektów projektu. Fabryka projektu jest podobna do standardowej fabryki klas dla współtworzących obiektów COM. Jednak obiekty projektu nie można współistnieć. mogą być tworzone tylko przy użyciu fabryki projektu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE wywołuje fabrykę projektu zaimplementowaną w pakietu VSPackage, gdy użytkownik załaduje istniejący projekt lub utworzy nowy projekt w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Nowy obiekt projektu zapewnia IDE z wystarczającą ilością informacji do wypełnienia **Eksplorator rozwiązań**. Nowy obiekt projektu udostępnia również interfejsy wymagane do obsługi wszystkich odpowiednich akcji interfejsu użytkownika inicjowanych przez środowisko IDE.

 Interfejs można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> w klasie w projekcie. Zazwyczaj znajduje się on w osobnym module.

 Projekty, które obsługują agregowanie przez właściciela, muszą utrwalać klucz właściciela w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Metoda jest wywoływana w projekcie z kluczem właściciela, posiadany projekt konwertuje swój klucz właściciela na identyfikator GUID fabryki projektu, a następnie wywołuje `CreateProject` metodę w tej fabryce projektu, aby wykonać rzeczywiste tworzenie.

## <a name="create-an-owned-project"></a>Tworzenie projektu należącego do użytkownika
 Właściciel tworzy projekt należący do dwóch faz:

1. Przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Zapewnia to, że właścicielem projektu jest szansa na utworzenie zagregowanego obiektu projektu na podstawie kontroli danych wejściowych `IUnknown` . Właścicielem projektu jest przekazanie wewnętrznego `IUnknown` i zagregowanego obiektu z powrotem do projektu będącego właścicielem. Dzięki temu projekt będzie miał szansę na przechowywanie danych wewnętrznych `IUnknown` .

2. Przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Posiadany projekt wykonuje wszystkie jego wystąpienia, gdy ta metoda jest wywoływana zamiast wywoływania metody `IVsProjectFactory::CreateProject` , tak jak w przypadku projektów, które nie należą do siebie. Wyliczenie danych wejściowych `VSOWNEDPROJECTOBJECT` jest zazwyczaj zagregowanym projektem. Posiadany projekt może używać tej zmiennej do określenia, czy obiekt projektu został już utworzony (plik cookie nie jest równy NULL) lub musi być utworzony (plik cookie ma wartość NULL).

   Typy projektów są identyfikowane przez unikatowy identyfikator GUID projektu, podobny do identyfikatora CLSID obiektu COM, który można współtworzyć. Zazwyczaj jedna fabryka projektu obsługuje tworzenie wystąpień pojedynczego typu projektu, chociaż istnieje możliwość, że jedna fabryka projektu ma więcej niż jeden identyfikator GUID typu projektu.

   Typy projektów są skojarzone z określonym rozszerzeniem nazwy pliku. Gdy użytkownik próbuje otworzyć istniejący plik projektu lub próbuje utworzyć nowy projekt przez sklonowanie szablonu, IDE używa rozszerzenia na pliku, aby określić odpowiedni identyfikator GUID projektu.

   Gdy tylko środowisko IDE określi, czy należy utworzyć nowy projekt, czy otworzyć istniejący projekt określonego typu, IDE używa informacji w rejestrze systemowym w obszarze **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** , aby sprawdzić, które pakietu VSPackage implementuje wymaganą fabrykę projektu. IDE ładuje ten pakietu VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodzie pakietu VSPackage musi zarejestrować swoją fabrykę projektu przy użyciu IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metodę.

   Podstawową metodą `IVsProjectFactory` interfejsu jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , która powinna obsługiwać dwa scenariusze: Otwieranie istniejącego projektu i tworzenie nowego projektu. Większość projektów przechowuje swój stan projektu w pliku projektu. Zwykle nowe projekty są tworzone przez utworzenie kopii pliku szablonu przekazaną do `CreateProject` metody, a następnie otwarcie kopii. Istniejące projekty są tworzone przez bezpośrednie otwarcie pliku projektu przesłanego do `CreateProject` metody. W `CreateProject` razie potrzeby Metoda może wyświetlać dodatkowe funkcje interfejsu użytkownika.

   Projekt może również korzystać z braku plików, a zamiast tego przechowywać jego stan projektu w mechanizmie magazynu innym niż system plików, na przykład baza danych lub serwer sieci Web. W takim przypadku parametr nazwy pliku przesłany do `CreateProject` metody nie jest w rzeczywistości ścieżką systemu plików, ale unikatowym ciągiem — adresem URL, aby zidentyfikować dane projektu. Nie trzeba kopiować plików szablonów, które są przesyłane do programu, `CreateProject` Aby wyzwolić odpowiednią sekwencję konstrukcyjną do wykonania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
