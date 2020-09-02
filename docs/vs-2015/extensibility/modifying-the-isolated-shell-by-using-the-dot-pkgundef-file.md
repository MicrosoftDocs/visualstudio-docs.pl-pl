---
title: Modyfikowanie izolowanej powłoki przy użyciu. Plik PKGUNDEF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538397"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modyfikowanie programu Isolated Shell przy użyciu pliku Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmodyfikować plik. pkgundef, aby wykluczyć określone wpisy rejestru z aplikacji izolowanej powłoki. Zazwyczaj podczas pierwszego uruchomienia aplikacji na komputerze powłoka programu Visual Studio kopiuje istniejące wpisy rejestru programu Visual Studio do głównego klucza rejestru aplikacji. Obejmuje to wszystkie odwołania do aktualnie zainstalowanych pakietów VSPackage.  
  
 Aby wykluczyć określony wpis rejestru z aplikacji izolowanej powłoki, należy dodać do pliku Application. pkgundef klucz pakietu, a następnie wpis. Klucze i wpisy są reprezentowane podobnie jak w pliku. pkgdef; oznacza to, że jako [$RootKey $] lub [$RootKey $ \\ *podklucz*] i "*entry*" =*Value*, gdzie *podklucz* jest podkluczem, który ma wpływ, *wpis* jest wpisem do usunięcia, a *wartość* jest albo `""` `dword:00000000` .  
  
 Aby wykluczyć wiele wpisów z klucza rejestru, po prostu Wyświetl klucz za jeden raz, a następnie wiersz dla każdego wpisu do wykluczenia.  
  
 Aby wykluczyć cały klucz rejestru z aplikacji izolowanej powłoki, Dodaj klucz do pliku Application. pkgundef, ale nie określaj żadnych wpisów rejestru dla tego klucza.  
  
 Do pliku. pkgundef można dodawać komentarze. Komentarz jednowierszowy musi mieć dwa ukośniki jako pierwsze dwa znaki.  
  
 Na przykład aby usunąć polecenie **Połącz z bazą danych** i **nawiązać połączenie** z poleceniami r w menu **Narzędzia** , można odkomentować wiersz:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 i Dodaj wiersz:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 do pliku. pkgundef aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory GUID pakietu funkcji programu Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Dostosowywanie programu Shell (izolowanego)](../extensibility/customizing-the-isolated-shell.md)
