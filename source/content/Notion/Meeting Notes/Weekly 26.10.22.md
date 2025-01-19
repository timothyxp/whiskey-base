---
Created: 2022-10-25T13:14
Last Edited Time: 2022-10-31T15:08
Type: Weekly Sync
Created By: Тимофей Смирнов
---
## Показать

- тикет
- способы бенчмарка памяти, не работал enable-resource-vars, allow_groth, log work

  

## База

- еще допроверить Tensor V, паралельно экспы считаются  
    Чекнул скейлы, lr and decay. output scale -  
    Для LAMB надо дофиксить  
    
- ytensorflow импорты через try-except
- впилить логи про память, про loss scale и grad_accum

  

## Гипотезы

- [ ] CUDA 11.8
- [ ] bfloat16