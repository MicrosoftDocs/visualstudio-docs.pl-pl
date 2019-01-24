---
title: Modyfikowanie programu Isolated Shell przy użyciu. Pliku Pkgundef | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801997"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modyfikowanie programu Isolated Shell przy użyciu. Pliku Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmodyfikować pliku pkgundef, aby wykluczyć wpisy rejestru określonego z aplikacji isolated shell. Zazwyczaj podczas pierwszego uruchomienia aplikacji na komputerze, powłoki programu Visual Studio kopiuje istniejące wpisy rejestru programu Visual Studio do głównego klucza rejestru dla aplikacji. Obejmuje to wszystkie odwołania do VSPackages aktualnie zainstalowany.  
  
 Aby wykluczyć określony wpis rejestru z aplikacji isolated shell, Dodaj do pliku pkgundef aplikacji klucza pakietu następuje zapis. Klucze i wpisy, które są reprezentowane podobnie jak w pliku .pkgdef. oznacza to jak [$RootKey$] lub [$RootKey$\\*podklucz*] i "*wpis*" =*wartość*, gdzie *podklucz* jest podklucza który wpływa na, *wpis* wpis do usunięcia, a *wartość* jest `""` lub `dword:00000000`.  
  
 Aby wykluczyć wiele wpisów z klucza rejestru, po prostu lista klucz jeden raz, następuje jeden wiersz dla każdego wpisu, które mają zostać wykluczone.  
  
 Aby wykluczyć klucz rejestru całego z aplikacji isolated shell, Dodaj klucz do pliku pkgundef aplikacji, ale nie określono żadnych wpisów rejestru dla tego klucza.  
  
 Można dodać komentarze do pliku pkgundef. Komentarz jednowierszowy musi mieć dwa ukośniki jako dwa pierwsze znaki.  
  
 Na przykład, aby usunąć **Połącz z bazą danych** i **nawiązywanie połączenia z serwerem r** polecenia na **narzędzia** menu można usuń znaczniki komentarza:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 i Dodaj wiersz:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 do pliku pkgundef aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory GUID pakietów funkcji programu Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md)
