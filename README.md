# Milestone2.0
def find_splice(dna_motif,dna):
   result = []
   start = 0
   for x in range(len(dna_motif)):
        while dna[start] != dna_motif[x]:
            start += 1
        result.append(start)
   return result
   
def shared_motif(dna_list):
  dna0 = dna_list[0]
  substr = ''
  if len(dna_list) > 1 and len(dna0) > 0:
    for i in range(len(dna0)):
      for j in range(len(dna0)-i+1):
        if j > len(substr) and is_substr(dna0[i:i+j], dna_list):
          substr = dna0[i:i+j]
    return substr
def is_substr(find, data):
  if len(data) < 1 and len(find) < 1:
    return False
  for i in range(len(data)):
    if find not in data[i]:
      return False
  return True
  
def get_edges(dna_dict):
  adjacent_list = []
  for key1, dna1 in dna_dict.items():
    for key2, dna2 in dna_dict.items():
      if key1 != key2 and dna1[-3:] == dna2 [:3]:
        adjacent_list.append((key1,key2))
  return adjacent_list
