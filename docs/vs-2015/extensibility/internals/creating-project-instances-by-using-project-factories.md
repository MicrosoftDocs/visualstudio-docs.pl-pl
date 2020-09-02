---
title: Tworzenie wystąpień projektu przy użyciu fabryk projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f26b11aaf74b73535c82ebcd6422f3be0bba3f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697204"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektów przy użyciu fabryk projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typy projektów w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wykorzystują *fabrykę projektu* do tworzenia wystąpień obiektów projektu. Fabryka projektu jest podobna do standardowej fabryki klas dla współtworzących obiektów COM. Jednak obiekty projektu nie mogą być współtworzone: można je tworzyć tylko przy użyciu fabryki projektu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE wywołuje fabrykę projektu zaimplementowaną w pakietu VSPackage, gdy użytkownik załaduje istniejący projekt lub utworzy nowy projekt w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Nowy obiekt projektu zapewnia IDE z wystarczającą ilością informacji do wypełnienia Eksplorator rozwiązań. Nowy obiekt projektu udostępnia również interfejsy wymagane do obsługi wszystkich odpowiednich akcji interfejsu użytkownika inicjowanych przez środowisko IDE.  
  
 Interfejs można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> w klasie w projekcie. Zazwyczaj znajduje się on w osobnym module.  
  
 Przykład implementacji `IVsProjectFactory` interfejsu można znaleźć w PrjFac. cpp, który znajduje się w katalogu podstawowym przykładowym [projektu](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) .  
  
 Projekty, które obsługują agregowanie przez właściciela, muszą utrwalać klucz właściciela w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Metoda jest wywoływana w projekcie z kluczem właściciela, posiadany projekt konwertuje swój klucz właściciela na identyfikator GUID fabryki projektu, a następnie wywołuje `CreateProject` metodę w tej fabryce projektu, aby wykonać rzeczywiste tworzenie.  
  
## <a name="creating-an-owned-project"></a>Tworzenie projektu należącego do użytkownika  
 Właściciel tworzy projekt należący do dwóch faz:  
  
1. Przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Zapewnia to, że właścicielem projektu jest szansa na utworzenie zagregowanego obiektu projektu na podstawie kontroli danych wejściowych `IUnknown` . Właścicielem projektu jest przekazanie wewnętrznego `IUnknown` i zagregowanego obiektu z powrotem do projektu będącego właścicielem. Dzięki temu projekt będzie miał szansę na przechowywanie danych wewnętrznych `IUnknown` .  
  
2. Przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Posiadany projekt wykonuje wszystkie jego wystąpienia, gdy ta metoda jest wywoływana zamiast wywoływania metody `IVsProjectFactory::CreateProject` , tak jak w przypadku projektów, które nie należą do siebie. Wyliczenie danych wejściowych `VSOWNEDPROJECTOBJECT` jest zazwyczaj zagregowanym projektem. Posiadany projekt może używać tej zmiennej do określenia, czy obiekt projektu został już utworzony (plik cookie nie jest równy NULL) lub musi być utworzony (plik cookie ma wartość NULL).  
  
   Typy projektów są identyfikowane przez unikatowy identyfikator GUID projektu, podobny do identyfikatora CLSID obiektu COM, który można współtworzyć. Zazwyczaj jedna fabryka projektu obsługuje tworzenie wystąpień pojedynczego typu projektu, chociaż istnieje możliwość, że jedna fabryka projektu ma więcej niż jeden identyfikator GUID typu projektu.  
  
   Typy projektów są skojarzone z określonym rozszerzeniem nazwy pliku. Gdy użytkownik próbuje otworzyć istniejący plik projektu lub próbuje utworzyć nowy projekt przez sklonowanie szablonu, IDE używa rozszerzenia na pliku, aby określić odpowiedni identyfikator GUID projektu.  
  
   Gdy tylko środowisko IDE określi, czy należy utworzyć nowy projekt, czy otworzyć istniejący projekt określonego typu, IDE używa informacji w rejestrze systemowym w obszarze [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0\Projects], aby znaleźć, który pakietu VSPackage implementuje wymaganą fabrykę projektu. IDE ładuje ten pakietu VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodzie pakietu VSPackage musi zarejestrować swoją fabrykę projektu przy użyciu IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metodę.  
  
   Podstawową metodą `IVsProjectFactory` interfejsu jest, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> która powinna obsługiwać dwa scenariusze: Otwieranie istniejącego projektu i tworzenie nowego projektu. Większość projektów przechowuje swój stan projektu w pliku projektu. Zwykle nowe projekty są tworzone przez utworzenie kopii pliku szablonu przekazaną do `CreateProject` metody, a następnie otwarcie kopii. Istniejące projekty są tworzone przez bezpośrednie otwarcie pliku projektu przesłanego do `CreateProject` metody. W `CreateProject` razie potrzeby Metoda może wyświetlać dodatkowe funkcje interfejsu użytkownika.  
  
   Projekt może również korzystać z braku plików, a zamiast tego przechowywać jego stan projektu w mechanizmie magazynu innym niż system plików, na przykład baza danych lub serwer sieci Web. W takim przypadku parametr nazwy pliku przesłany do `CreateProject` metody nie jest w rzeczywistości ścieżką systemu plików, ale unikatowym ciągiem — adresem URL, aby zidentyfikować dane projektu. Nie trzeba kopiować plików szablonów, które są przesyłane do programu, `CreateProject` Aby wyzwolić odpowiednią sekwencję konstrukcyjną do wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
