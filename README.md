# pacman-search
- Q1: Depth First Search 
  + Khởi tạo vị trí bắt đầu và thêm vào Stack (LIFO)
  + Sử dụng Stack để lưu lại state, state này bao gồm một node và actions dẫn đến node đó
  + Khởi tạo một mảng lưu lại các node đã đi qua, gọi là visitedNodes
  + Lần lượt lấy một state ra khỏi Stack cho đến khi hết hoặc đến khi tìm được đích
    + Trả về actions tại đây nếu node đang xét là đích
    + Ngược lại, nếu node đang xét chưa được đi qua thì thêm node đó vào visitedNodes.
      + Sinh ra state tiếp theo rồi lại thêm vào Stack
     
- Q2: Breadth First Search
  + Khởi tạo vị trí bắt đầu và thêm vào Queue (FIFO)
  + Sử dụng Queue để lưu lại state, state này bao gồm một node và actions dẫn đến node đó
  + Khởi tạo một mảng lưu lại các node đã đi qua, gọi là visitedNodes
  + Lần lượt lấy một state ra khỏi Queue cho đến khi hết hoặc đến khi tìm được đích
    + Trả về actions tại đây nếu node đang xét là đích
    + Ngược lại, nếu node đang xét chưa được đi qua thì thêm node đó vào visitedNodes.
      + Sinh ra state tiếp theo rồi lại thêm vào Queue
      
- Q3: Uniform Cost Search
  + Khởi tạo vị trí bắt đầu và thêm vào PriorityQueue
  + Sử dụng PriorityQueue để lưu lại state và một priority, state này bao gồm một node, actions dẫn đến node đó, và giá để đến được node đó.
  + Khởi tạo một mảng lưu lại các node đã đi qua, gọi là visitedNodes
  + Lần lượt lấy một state ra khỏi Queue cho đến khi hết hoặc đến khi tìm được đích
    + Trả về actions tại đây nếu node đang xét là đích
    + Ngược lại, nếu node đang xét chưa được đi qua thì thêm node đó vào visitedNodes.
      + Sinh ra state tiếp theo, còn priority thì gán bằng giá để đến node tiếp theo rồi lại thêm vào PriorityQueue
      
- Q4: A* Search
  + Khởi tạo vị trí bắt đầu và thêm vào PriorityQueue
  + Sử dụng PriorityQueue để lưu lại state và một heuristicCost, state này bao gồm một node, actions dẫn đến node đó, và giá để đến được node đó.
  + Khởi tạo một mảng lưu lại các node đã đi qua, gọi là visitedNodes
  + Lần lượt lấy một state ra khỏi Queue cho đến khi hết hoặc đến khi tìm được đích
    + Trả về actions tại đây nếu node đang xét là đích
    + Ngược lại, nếu node đang xét chưa được đi qua thì thêm node đó vào visitedNodes.
      + heuristicCost = tổng của giá để đến node tiếp theo + giá ước tính để đến đích gần nhất
      + Sinh ra state tiếp theo rồi lại thêm vào PriorityQueue
      
- Q5: Corners Problem: Representation
  + Hàm getStartState chỉ cần trả về vị trí bắt đầu và danh sách các góc đã qua
  + Hàm isGoalState:
    + Lấy ra node hiện tại (currentNode) và danh sách các góc đã đi qua (visitedNodes)
    + Nếu currentNode là góc thì:
      + Thêm vào visitedNodes nếu chưa đi qua
      + Tại đây, trả về True nếu đã đi qua đủ 4 góc. Ngược lại, trả về False
    + Nếu currentNode không phải góc thì trả về False
  + Hàm getSuccessor:
    + Lần lượt xét 4 action để tính vị trí node tiếp theo:
      + Lấy ra danh sách các góc đã đi qua (visitedNodes) và tọa độ x, y hiện tại để tính tọa độ node tiếp theo dựa theo action
      + Nếu là tường thì bỏ qua và xét action tiếp theo
      + Ngược lại:
        + Nếu node tiếp theo là góc và chưa đi qua thì thêm vào visitedNodes
        + Lấy giá trị successor bao gồm (node tiếp theo,visitedNodes), action đang xét và giá = 1 
        
- Q6: Corners Problem: Heuristic
  + Nếu state hiện tại là đích thì trả về cornerHeuristic = 0
  + Lấy danh sách các node đã qua (vistedCorners), và node hiện tại
  + Khởi tạo danh sách các node chưa đi qua (notVistedCorners), thêm các góc không nằm trong vistedCorners
  + Trả về cornerHeuristic bằng khoảng cách manhattan từ node hiện tại đến góc xa nhất
  
- Q7: Eating All The Dots: Heuristic
  + Nếu state hiện tại là đích thì trả về foodHeuristic = 0
  + Trả về foodHeuristic bằng khoảng cách maze từ node hiện tại đến food xa nhất
  
- Q8: Suboptimal Search
