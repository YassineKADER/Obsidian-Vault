```Java
package exMyClass;

public class Complex {
	private double real;
	private double img;

	public Complex() {
		this.real = 0;
		this.img = 0;
	}

	public Complex(double realPart, double imaginaryPart) {

		this.real = realPart;
		this.img = imaginaryPart;
	}

	public Complex add(Complex othnbr) {
		return new Complex(this.real + othnbr.real, this.img + othnbr.img);
	}

	public Complex substract(Complex othnbr) {
		return new Complex(this.real - othnbr.real, this.img - othnbr.img);
	}

	public Complex multiply(Complex othnbr) {
		return new Complex((this.real * othnbr.real) - (this.img * othnbr.img),
				(this.img * othnbr.real) + (this.real * othnbr.img));
	}

	public Complex div(Complex nbr) {
		return new Complex(
				(this.real * nbr.real) + (this.img * nbr.img) / (Math.pow(nbr.real, 2.0) + Math.pow(nbr.img, 2.0)),
				(this.real * nbr.img) + (this.img * nbr.real) / (Math.pow(nbr.real, 2.0) + Math.pow(nbr.img, 2.0)));
	}

	public void setRealPart(double real) {
		this.real = real;
	}

	public void setImgPart(double img) {
		this.img = img;
	}

	public double getRealPart() {
		return this.real;
	}

	public double getImgPart() {
		return this.img;
	}

	@Override
	public String toString() {
		if (img >= 0)
			return this.getRealPart() + "+" + this.getImgPart() + "i";
		else
			return this.getRealPart() + "" + this.getImgPart() + "i";
	}
}
```

  

  

```Java
package controle;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Comparator;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;
import java.util.TreeMap;

public class Agence {
	private String nom;
	private ListVoitures vs;
	private Map<Client, ListVoitures> clientVoitureL;

	public Agence(String nom) {
		this.nom = nom;
		this.vs = new ListVoitures();
		this.clientVoitureL = new HashMap<Client, ListVoitures>();
	}

	public void ajoutVoiture(Voiture obj) {
		this.vs.ajoutVoiture(obj);
	}

	public void supprimerVoiture(Voiture obj) {
		this.vs.supprimerVoiture(obj);
	}

	public void loueClientVoiture(Client cl, Voiture v) {
	  	if(clientVoitureL.containsKey(cl)) {
		for (Entry x : clientVoitureL.entrySet()) {
			if (x.getKey().equals(cl)) {
				((ListVoitures) x.getValue()).ajoutVoiture(v);
			}
		}
		}
		else{
			ListVoitures  lv = new ListVoitures();
			lv.ajoutVoiture(v);
			clientVoitureL.put(cl, lv);
		}
	}

	public void retourClient(Client cl, Voiture v) {
		for (Entry x : clientVoitureL.entrySet()) {
			if (x.getKey().equals(cl)) {
				((ListVoitures) x.getValue()).supprimerVoiture(v);
			}
		}
	}

	
	public List<Voiture> selectVoitureSelonCritier(Critere obj) {
		List<Voiture> list = new ArrayList<Voiture>();
		Iterator it = this.vs.iterator();
		while(it.hasNext()) {
			if(obj.estSatisfaitPar((Voiture)it.next())) 
				list.add((Voiture)it.next()); 
		}
		return list;
	}
	
	public Set<Client> ensembleClientLoueurs(){
		return this.clientVoitureL.keySet();
	}
	
	public Collection<ListVoitures> collectionVoituresLouees(){
		return this.clientVoitureL.values();
	}
	
	public void afficheLesClientsEtLeursListsVoitures() {
		for(Entry<Client, ListVoitures> x : this.clientVoitureL.entrySet()) {
			System.out.println(x.getKey().toString());
			x.getValue().afficher();
		}
	}
	
	public Map<Client, ListVoitures> trieCodeCroissant(){
		TreeMap<Client, ListVoitures> returned = new TreeMap<Client, ListVoitures>(Comparator.comparing(Client::getCode));
		
		return returned;
	}
	
	public Map<Client, ListVoitures> trieNomCroissant(){
		TreeMap<Client, ListVoitures> returned = new TreeMap<Client, ListVoitures>(Comparator.comparing(Client::getNom));
		return returned;
		
	}
}
```