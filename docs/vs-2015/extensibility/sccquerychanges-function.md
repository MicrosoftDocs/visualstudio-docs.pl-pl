---
title: Funkcja SccQueryChanges | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: baa6059a1668be5507994921cb96ac3ed1cfd5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200015"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja wylicza daną listę plików, dostarczając informacje o zmianach nazw poszczególnych plików za pośrednictwem funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 podczas Wskaźnik kontekstu wtyczki kontroli źródła.  
  
 nFiles  
 podczas Liczba plików w `lpFileNames` tablicy.  
  
 lpFileNames  
 podczas Tablica nazw plików, dla których mają zostać wyświetlone informacje.  
  
 pfnCallback  
 podczas Funkcja wywołania zwrotnego do wywołania dla każdej nazwy pliku na liście (zobacz [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) , aby uzyskać szczegółowe informacje).  
  
 pvCallerData  
 podczas Wartość, która zostanie przeniesiona bez zmian do funkcji wywołania zwrotnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Proces zapytania został ukończony pomyślnie.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|  
|SCC_E_NONSPECIFICERROR|Wystąpił błąd nieokreślony lub ogólny.|  
  
## <a name="remarks"></a>Uwagi  
 Zmiany, których dotyczy zapytanie, są w przestrzeni nazw: w przypadku, zmiana nazwy, dodanie i usunięcie pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Kody błędów](../extensibility/error-codes.md)
