class Exercise
{
	static int Main()
	{
		ListOfParts Parts = new ListOfParts();
		CarPart     Part;

		Part  = new CarPart();
		Part.PartNum = 9743;
		Part.PartName = "Air Filter";
		Part.PartCost  = 8;
		Parts.Add(Part);
	
		Part  = new CarPart();
		Part.PartNum = 27487;
		Part.PartName = "Clutch Disk";
		Part.PartCost  = 47;
		Parts.Add(Part);
		Console.WriteLine("Number of Parts: {0}", Parts.Count);
		
		for(int i = 0; i < Parts.Count; i++)
		{
			CarPart part = Parts.Retrieve(i);
			Console.WriteLine("\nCar Part Information");
			Console.WriteLine("Part #:      {0}", part.PartNum);
			Console.WriteLine("Description: {0}", part.PartName);
			Console.WriteLine("Unit Price: Rs {0:}", part.PartCost);
		}

		return 0;
	
	}

class CarPart
{

public int PartNum;
public string PartName;
public int PartCost;
public CarPart Next;
};


class ListOfParts

{
private int _size;
public ListOfParts()
	{
	_size=0;
	Head=null;
	}
	public int Count
	{
	get{return _size;}
	
	}
	public CarPart Head;
	
	public int Add(CarPart NewItem)
	{
		CarPart Sample = new CarPart();

		Sample      = NewItem;
		Sample.Next = Head;
		Head        = Sample;
		return _size++;
	}
	
	public CarPart Retrieve(int Position)
	{
		CarPart Current = Head;

		for(int i = 0; i < Position && Current != null; i++)
			Current = Current.Next;
		return Current;
	}
}
}
