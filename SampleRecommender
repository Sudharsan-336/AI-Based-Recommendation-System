package codtech;

import org.apache.mahout.cf.taste.impl.model.file.FileDataModel;
import org.apache.mahout.cf.taste.model.DataModel;
import org.apache.mahout.cf.taste.similarity.UserSimilarity;
import org.apache.mahout.cf.taste.impl.similarity.PearsonCorrelationSimilarity;
import org.apache.mahout.cf.taste.neighborhood.UserNeighborhood;
import org.apache.mahout.cf.taste.impl.neighborhood.NearestNUserNeighborhood;
import org.apache.mahout.cf.taste.recommender.Recommender;
import org.apache.mahout.cf.taste.impl.recommender.GenericUserBasedRecommender;
import org.apache.mahout.cf.taste.recommender.RecommendedItem;
import org.apache.mahout.cf.taste.impl.common.LongPrimitiveIterator;

import java.io.File;
import java.util.List;

public class SampleRecommender {

    public static void main(String[] args) throws Exception {
        // Path to sample data
        String path = "data/ratings.csv";
        if (args.length >= 1) path = args[0];

        DataModel model = new FileDataModel(new File(path));

        // Use Pearson similarity (other options: EuclideanDistanceSimilarity, LogLikelihood)
        UserSimilarity similarity = new PearsonCorrelationSimilarity(model);

        // Choose neighborhood size (k nearest neighbors)
        int neighborhoodSize = 2;
        UserNeighborhood neighborhood = new NearestNUserNeighborhood(neighborhoodSize, similarity, model);

        // Build the recommender
        Recommender recommender = new GenericUserBasedRecommender(model, neighborhood, similarity);

        System.out.println("\n=== Recommendations (top 5 per user) ===\n");
        LongPrimitiveIterator userIt = model.getUserIDs();
        while (userIt.hasNext()) {
            long userId = userIt.nextLong();
            List<RecommendedItem> recs = recommender.recommend(userId, 5);
            System.out.printf("User %d -> ", userId);
            if (recs.isEmpty()) {
                System.out.println("(no recommendations)");
            } else {
                for (RecommendedItem r : recs) {
                    System.out.printf("[item:%d,score:%.3f] ", r.getItemID(), r.getValue());
                }
                System.out.println();
            }
        }

        // Example: estimate preference for a user-item pair
        long testUser = 1L, testItem = 104L;
        try {
            float estimate = recommender.estimatePreference(testUser, testItem);
            System.out.printf("\nEstimated preference for user %d on item %d = %.3f\n", testUser, testItem, estimate);
        } catch (Exception e) {
            System.out.println("Could not estimate preference: " + e.getMessage());
        }
    }
}

